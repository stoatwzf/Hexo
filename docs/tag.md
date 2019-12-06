# 标签插件

标签插件和`Front-matter`中的标签不同，他们是用于在文章中快速插入特定内容的插件。

## 引用块

在文章中插入引言，可以包含作者、来源和标题

	{% blockquote [author[, source]] [link] [source_link_title] %}
	content
	{% endblockquote %}

引用书上的句子

	{% blockquote author, source %}
	content
	{% endblockquote %}

引用**Twitter**

	{% blockquote @author url%}
	content
	{% endblockquote %}

引用网络上的文章

	{% blockquote author url%}
	content
	{% endblockquote %}

## 代码块

在文章中插入代码

	{% codeblock [title] [lang: language] [url] [link text] %}
	code
	{% endcodeblock %}

普通的代码块

	{% codeblock %}
	code
	{% endcodeblock %}

指定语言

	{% codeblock lang: objc %}
	code
	{% endcodeblock %}

附加说明

	{% codeblock Array.map %}
	code
	{% endcodeblock %}

附加说明和网址

	{% codeblock _.compact http://underscorejs.com %}
	code
	{% endcodeblock %}

## 反引号代码块

另一种形式的代码块，不同的是它使用三个反引号来包裹

	```[language] [title] [url] [link text] code```

## Pull Quote

在文章中插入`Pull quote`

	{% pullquote [class] %}
	content
	{% endpullquote %}

## jsFiddle

在文章中插入`jsFiddle`

	{% jsfiddle shorttag [tabs] [skin] [width] [height] %}

## Gist

在文章中插入`Gist`

	{% gist gist_id [filename] %}

## iframe

在文章中嵌入`iframe`

	{% iframe url [width] [height] %}

## image

在文章中插入指定大小的图片

	{% img [class name] path [width] [height] title %}

## link

在文章中插入链接

	{% link text url [external] [title] %}

## include Code

插入`source/downloads/code`文件夹内的代码文件。`source/downloads/code`不是固定的，取决于你在配置文件中`code_dir`的配置

	{% include_code [title] [lang:language] [from:line] [to:line] path %}

## Youtube

在文章中插入`Youtube`视频

	{% youtube vide_id %}

## Vimeo

在文章中插入`Vimeo`视频

	{% vimeo video_id %}

## 引用文章

引用其他文章的链接

	{% post_link filename [title] [escape] %}

## 引用资源

引用文章的资源

	{% asset_path filename [title] [escope] %}

## Raw

在文章中插入`Swig`标签

	{% raw %}
	content
	{% endraw %}

## 文章摘要和截断

在文渣中使用`<!-- more -->`，那么`<!-- more -->`之前的文字将会被视为摘要.

	content
	<!-- more -->
	content