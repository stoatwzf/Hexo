# 配置

你可以在`_config.yml`中修改大部分的配置

## 网站

| 参数 | 描述 |
| --- | --- |
| title | 网站标题 |
| subtitle | 网站副标题 |
| description | 网站描述 |
| keywords | 网站的关键词。使用半角逗号,分隔多个关键词 |
| author | 作者 |
| language | 网站使用的语言 |
| timezone | 网站时区 |

## 网址

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| url | 网址 |
| root | 网站根目录 |
| permalink | 文章的永久链接格式 | :year/:month/:day/:title/ |
| permalink_defaults | 永久链接中各部分的默认值 |
| pretty_urls | 改写 `pemalink` 的值来美化 URL |
| pretty_urls.trailing_index | 是否在永久链接中保留尾部的 `index.html` | true |

> 如果你的网站存放在子目录中，例如 `http://yoursite.com/blog`, 则请将你的 `url` 设为 `http://yoursite.com/blog` 并把 `root` 设为 `/blog/`

## 目录 

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| source_dir | 资源文件夹 | source |
| public_dir | 公共文件夹 | public |
| tag_dir | 标签文件夹 | tags |
| archive_dir | 归档文件夹 | archives |
| category_dir | 分类文件夹 | categories |
| code_dir | include code 文件夹，source_dir 下的子目录 | downloads/code |
| i18n_dir | 国际化（i18n）文件夹 | :lang |
| skip_render | 跳过指定文件的渲染

## 文章

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| new_post_name | 新文章的文件名称 | :title.md |
| default_layout | 预设布局 | post |
| auto_spacing | 在中文和英文之间加入空格 | false |
| titlecase | 把标题转换为 title case | false |
| external_link | 在新标签中打开链接 | true |
| external_link.enable | 在新标签中打开链接 | true |
| external_link.field | 对整个网站生效或者文章 | site |
| external_link.exclude | 需要排除的域名 | [] |
| filename_case | 把文件名转化为大小写 | 0 |
| render_drafts | 显示草稿 | false |
| post_asset_folder | 启用 Asset 文件夹 | false |
| relative_link | 把链接改为与根目录的相对地址 | false |
| future | 显示未来的文章 | true |
| highlight | 代码块的设置 |
| highlight.enable | 开启代码块高亮 | true |
| highlight.auto_detect | 如果未指定语言，则启用自动检查 | false |
| highlight.line_number | 显示行数 | true |
| highlight.tab_replace | 用n个空格替换tabs | '' |

> ## 相对地址
默认情况下，Hexo 生成的超链接都是绝对地址。例如，如果您的网站域名为 example.com,您有一篇文章名为 hello，那么绝对链接可能像这样：http://example.com/hello.html，它是绝对于域名的。相对链接像这样：/hello.html，也就是说，无论用什么域名访问该站点，都没有关系，这在进行反向代理时可能用到。通常情况下，建议使用绝对地址。

## 分类 & 标签

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| default_category | 默认分类 | uncategorized |
| category_map | 分类别名 |
| tag_map | 标签别名 |

## 日期 / 时间格式

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| date_format | 日期格式 | YYYY-MM-DD |
| time_format | 时间格式 | HH:mm:ss |
| use_date_for_updated | post.updated 将会使用 date 的值而不是文件的创建时间。在 Git 工作流中这个选项会很有用 | true |

## 分页

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| per_page | 每页显示的文章量（0 = 关闭分页） | 10 |
| pagination_dir | 分页目录 | page |

## 扩展

| 参数 | 描述 |
| --- | --- |
| theme | 当前主题名称。（false = 禁用主题） |
| theme_config | 主题配置文件 |
| deploy | 部署配置 |
| meta_generator | Meta generator 标签 |

## 包含和不包含目录和文件

| 参数 | 描述 |
| --- | --- |
| include | Hexo 默认会忽略隐藏文件和文件夹（包括名称以 `_` 和 `.` 开头的文件和文件夹，`_posts` 和 `_data` 等目录除外）。通过设置此字段将使 Hexo 处理他们并将他们复制到 `source` |
| exclude | Hexo 会忽略这些文件和目录 |
| ignore | ignore files/folders |

## 使用命令配置文件

可以在 hexo-cli 中使用 `--config` 参数来指定自定义配置文件的路径。你可以使用一个或多个 `YAML` 或 `JSON` 文件的路径

	$ hexo server --config  custom.yml
	$ hexo generate --config custom.yml,custom2.json,custom3.yml
	$ hexo generate --config custom.yml,custom2.json