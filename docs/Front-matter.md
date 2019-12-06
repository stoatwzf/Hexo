# Front-matter

Front-matter 是文件最上方`---`分割的区域，用于指定个别文件的变量

	---
	title: Hello
	date: 2019-11-28 17:14:18
	---

以下是预先定义的参数，你可以在模版中使用这些参数值并加以利用

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| layout | 布局 |
| title | 标题 | 文章的文件名 |
| date | 建立日期 | 文件建立日期 |
| updated | 更新日期 | 文件更新日期 |
| comments | 开启文章的评论功能 | true |
| tags | 标签 |
| categories | 分类 |
| permalink | 覆盖文章网址 |
| keywords | 仅用于`meta`标签和`Open Graph`的关键字 |

## 分类和标签

只有文章支持分类和标签，你可以在`Front-matter`中设置

	categories:
	- Diary
	tags:
	- PS3
	- Games

## JSON Front-matter

除了YAML外，你也可以使用JSON来编写`Front-matter`,只要将`---`换成`;;;`

	"title": "hello world",
	"date": "2019-11-28 17:14:18"
	;;;