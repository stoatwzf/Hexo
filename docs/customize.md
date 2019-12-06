# 自定义

## 永久链接

你可以在`_config.yml`配置整个网站的永久链接或者在每篇文章的`Front-matter`中指定

	permalink: :year/:month/:day/:title/

可以使用的变量

| 变量 | 描述 |
| --- | --- |
| :year | 文章的发表年份(4位数) |
| :month | 文章的发表月份(2位数) |
| :i_month | 文章的发表月份(去掉开头的零) |
| :day | 文章发表的日期(2位数) |
| :i_day | 文章的发表的日期(去掉开头的零) |
| :title |} 文件的名称 |
| :post_title | 文章标题 |
| :id | 文章ID |
| :category | 分类(如果没有分类，则是`default_category`)配置信息 |

## 主题

创建 Hexo 主题非常容易，你只要在`themes`文件夹内，新增任意名称的文件夹，并修改`_config.yml`内的`theme`设定

一个主题可能会有一下的结构

	.
	├── _config.yml
	├── languages
	├── layout
	├── scripts
	└── source

| 文件 | 描述 |
| --- | --- |
| _config.yml | 主题的配置文件 |
| languages | 语言文件夹 |
| layout | 布局文件夹，默认`Swig`模版引擎，你可以安装`EJS`、`Haml`或`Jade`支持 |
| scripts | 脚本文件夹 |
| source | 资源文件夹，除了模版以外的`Asset`，例如`CSS`、`JavaScript`文件等，都应该放在这个文件夹中 |

## 模版

模版决定了网站内容的呈现方式，每个主题至少都包含一个`index`模版

| 模版 | 用途 | 回退 |
| --- | --- | --- |
| index | 首页 |
| post | 文章 | index |
| page | 分页 | index |
| archive | 归档 | index |
| category | 分类归档 | archive |
| tag | 标签归档 | archive |

## 局部模版

局部模版让你在不同模版之间共享相同的组件，例如页首（Header）、页脚（Footer）或者侧边栏（Sidebar）

	partial/header.ejs
	<h1 id="logo"><%= config.title %></h1>

	index.ejs
	<%- partial('partial/header') %>
	<div id="content">Home page</div>

生成

	<h1 id="logo">My Site</h1>
	<div id="content">Home page</div>

## 局部变量

你可以在局部模版中指定局部变量并使用

	partial/header.ejs
	<h1 id="logo"><%= title %</h1>

	index.ejs
	<%- partial('partial/header', { title: 'Hello World'}) %>
	<div id='content>Home page</div>

生成

	<h1 id="logo">Hello World</h1>
	<div id="content">Home page</div>

## 局部缓存

如果你的主题太过复杂，或者需要生成的文件量太过于庞大，可能会大幅度降低性能，除了简化主题外，你可以考虑 Hexo 2.7 新增的局部缓存功能

他可以用于页首、页脚、侧边栏等文件不常变动的位置

	<%- fragment_cache('header', function (){
		return '<header></header>'
	}) %>

如果你使用局部模版的话，可以更简单

	<%- partial('header', {}, {cache: true})%>

> `fragment_cache()`将会缓存第一次渲染结果