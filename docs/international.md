# 国际化

若要让你的网站以不同语言呈现，你可以使用国际化功能。请先在`_config.yml`中调整`language`设定

	language: zh-tw

	language:
	- zh-tw
	- en

## 语言文件

语言文件可以使用`YAML`或`JSON`编写，并放在主题文件夹中的`languages`文件夹

## 模版

在模版中，透过`__`或`_p`辅助函数，即可渠道翻译后的字符串，前者用于一般使用；而后者用于复数字符串

示例

	// en.yml
	index:
		title: Home
		add: Add
		video:
			zero: No videos
			one: One video
			other: %d videos

## 路径

你可以在`front-matter`中指定该页面的语言，也可以在`_config.yml`中修改`i18n_dir`设定

	i18n_dir: :lang