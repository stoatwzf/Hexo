# 辅助函数

辅助函数帮助你在模版中快速插入内容。辅助函数不能在源文件中使用

## 网址

在路径前加上根路径

  	<%- url_for(path, [option]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| relative | 是否输出相对链接 | config.relative_link 的值 |

示例

	_config.yml
	root: /blog/

	<%- url_for('/a/path') %>
	// /blog/a/path

取得与`from`相对的`to`路径

	<%- relative_url(from, to) %>

示例

	<%- relative_url('foo/bar/', 'css/style.css') %>

根据邮箱地址返回 Gravatar 头像 URL

	<%- gravatar(email, [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| s | 图片大小 | 80 |
| d | 默认值头像 |
| f | 强制使用默认值头像 |
| r | 头像等级限制 |

示例

	<%- gravatar('a@abc.com', { s: 40, d: 'https://via.placeholder.com/150' }) %>

在路径前加上根路径和域名。输出会被自动转码

	<%- full_url_for(path) %>

示例

	_config.yml
	url: https://example.com/blog

	<%- full_url_for('/a/path') %>
	// https://example.com/blog/a/path

## HTML标签

载入 CSS 文件

	<%- css(path, ...) %>

示例

	<%- css('style.css') %>
	<%- css(['style.css', 'screen.css']) %>

载入 JavaScript 文件

	<%- js(path, ...) %>

示例

	<%- js('script.js') %>
	<%- js(['script.js', 'gallery.js']) %>

插入链接

	<%- link_to(path, [text], [options]) %>

示例

	<%- link_to('http://www.google.com', 'Google', {external: true}) %>

插入电子邮箱链接

	<%- mail_to(path, [text], [options]) %>

| 参数 | 描述 |
| --- | --- |
| class | Class 名称 |
| id | ID |
| subject | 邮件主题 |
| cc | 抄送 |
| bcc | 密送 |
| body | 邮件内容 |

示例

	<%- mail_to('a@abc.com', 'Email') %>

插入图片

	<%- image_tag(path, [options]) %>

| 参数 | 描述 |
| --- | --- |
| alt | 图片的替代文字 |
| class | Class 名称 |
| id | ID |
| width | 图片宽度 |
| height | 图片高度 |

插入`favicon`

	<%- favicon_ta(path) %>

插入`feed`链接

	<%- feed_tag(path, [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| title | Feed标题 |
| type | Feed类型 | atom |

## 条件函数

检查`path`是否复合目前页面的网址

	<%- is_current(path, [strict]) %>

检查当前页面是否为首页

	<%- is_home() %>

检查当前页面是否为文章

	<%- is_post() %>

检查当前页面是否为独立页面

	<%- is_page() %>

检查当前页面是否为存档页面

	<%- is_archive() %>

检查当前页面是否为年度归档页面

	<%- is_year() %>

检查当前页面是否为月度归档页面

	<%- is_month() %>

检查当前页面是否为分类归档页面

	<%- is_category() %>

检查当前页面是否为标签归档页面

	<%- is_tag() %>

## 字符串处理

清除开头和结尾的空格

	<%- trim(string) %>

清除字符串中的 HTML 标签

	<%- strip_html(string) %>

把字符串转为正确的 Title case

	<%- titlecase(string) %>

使用 Markdown 解析字符串

	<%- markdown(str) %>

解析字符串

	<%- render(str, engine, [options]) %>

使每行的字符串长度不超过`length`。`length`预设为 80

	<%- word_wrap(str, [length]) %>

移除超过`length`长度的字符串。`length`的默认值使 30

	<%- truncate(text, length) %>

## 模版

载入其他模版文件，你可以在`locals`设定区域变量

	<%- partial(layout, [locals], [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| cache | 缓存 | false |
| only | 限制局部变量。在模版中只能使用`locals`中设定的变量 | false |

局部缓存。它储存局部内容，下次使用时就能直接使用缓存

	<%- fragment_cache(id, fn) %>

示例

	<%- fragment_cache('header', function (){
		return '<header></header>'
	}) %>

## 日期和时间

插入格式化日期

	<%- date(date, [format]) %>

示例

	<%- date(new Date(), 'YYYY/M/D') %>

插入 XML 格式的日期

	<%- date_xml(date) %>

示例

	<%- date_xml(Date.now()) %>

插入格式化的时间

	<%- time(date, [format]) %>

示例

	<%- time(Date.now(), 'h:mm:ss a') %>

插入格式化的日期和时间

	<%- full_date(date, [format]) %>

示例

	<%- full_date(new Date(), 'dddd, MMMM Do YYYY, h:mmm:ss a') %>

## 列表

 插入分类列表

	<%- list_categories([options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| orderby | 分类排序方式 | name |
| order | 分类排列顺序。1，asc 升序；-1，desc 降序 | 1 |
| show_count | 显示每个分类的文章总数 | true |
| style | 分类列表的显示方式 | list |
| separator | 分类间的分隔符号 | ，|
| depth | 要显示的分类层级。0 显示所有层级的分类；-1 显示所有层级不分层 | 0 |
| class | 分类列表的 class 名称 | category |
| transform | 改变分类名称显示方法的函数 |
| suffix | 为链接添加前缀 | None |

示例

	<%- list_categories(post.categories, {
		class: 'post-category',
		transform (str){
			return str.toUpperCase()
		}
	}) %>

插入标签列表

	<%- list_tags([options]) %>

| 选项 | 描述 | 默认值 |
| --- | --- | --- |
| orderby | 标签排列方式 | name |
| order | 标签排列顺序。1 asc 升序；-1 desc 降序 | 1 |
| show_count | 显示每个标签的文章总数 | true |
| style | 标签列表的显示方式 | list |
| separator | 标签间的分隔符号 | ，|
| class | 标签列表的 class 名称 | tag |
| transform | 改变标签名称显示方法的函数 |
| amount | 要显示的标签数量（0 = 无限制） | 0 |
| suffix | 为链接添加前缀 |

插入归档列表

	<%- list_archives([options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| type | 类型 | monthly |
| order | 排列顺序。1 asc 升序；-1 desc 降序 | 1 |
| show_count | 显示每个归档的文章总数 | true |
| format | 日期格式 | MMMMM YYYY |
| style | 归档列表的显示方式 | list |
| separator | 归档间的分隔符号 | ，|
| class | 归档列表的 class 名称 | archive |
| transform | 该拜年归档名称显示方法的函数 |

插入文章列表

	<%- list_posts([options]) %>


| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| orderby | 文章排列方式 | date |
| order | 文章排列顺序。1 asc 升序；-1 desc 降序 | -1 |
| style | 文章列表的显示方式 | list |
| separator | 文章间的分隔符号 | ，|
| class | 文章列表的 class 名称 | post |
| amount | 要显示的文章数量（0 = 无限制）| 6 |
| transform | 改变文章名称显示方式函数 |

插入标签云

	<%- tagcloud([tags], [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| min_font | 最小字体 | 10 |
| max_font | 最大字体 | 20 |
| unit | 字体尺寸单位 | px |
| amount | 标签总量 | 40 |
| orderby | 标签排列方式 | name |
| order | 标签排列顺序。1 asc 升序；-1 desc 降序 | 1 |
| color | 使用颜色 | false |
| start_color | 开始颜色 |
| end_color | 结束颜色 |

## 其他

插入分页链接

	<%- paginator(options) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| base | 基础网址 | / |
| format | 网址格式 | page/%d/ |
| total | 分页总数 | 1 |
| current | 目前页数 | 0 |
| prev_text | 上一页链接的文字 | Prev |
| next_text | 下一页链接的文字 | Next |
| space | 空白文字 | ... |
| prev_next | 显示上一页和下一页的链接 | true |
| end_size | 显示于两侧的页数 | 1 |
| mid_size | 显示与中间的页数 | 2 |
| show_all | 显示所有页数 | false |
| escape | Escape HTML tags | true |

示例

	<%- paginator({
		prev_text: '<',
		next_text: '>'
	}) %>

插入 Google 搜索框

	<%- search_form(options) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| class | 表单的 class name | search-form |
| text | 搜索提示文字 | Search |
| button | 显示搜索按钮 | false |

格式化数字

	<%- number_format(number, [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| precision | 数字精度 | false |
| delimiter |  千位数分隔符号 | ，|
| separator | 整数和小数之间的分隔符号 | ，|

示例

	<%- number_format(1222.67, {precision: 1})%>

插入 open graph 资源

	<%- open_graph([options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| title | 页面标题 | page.title |
| type | 页面类型 | blog |
| url | 页面网址 | url |
| image | 页面图片 | 内容中的图片 |
| site_name | 网站名称 | config.title |
| description | 页面描述 | 内容摘要或前 2000 字 |
| twitter_card | Twitter 卡片类型 | summary |
| twitter_id | Twitter ID |
| twitter_site | Twitter 网站 |
| google_plus | Google+ 个人资源链接 |
| fb_admins | Facebook 管理者 ID |
| fb_app_id | Facebook 应用程序 ID |

解析内容中的标题标签并插入目录

	<%- toc(str, [options]) %>

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| class | Class 名称 | toc |
| list_number | 显示编号 | true |

示例

	<%- toc(page.content) %>
