# 写作

你可以执行一下命令来创建一篇新文章或者新的页面

	$ hexo new [layout] <title>

## layout

Hexo 有三种默认布局：`post`、`page`、`draft`.

在创建这三种不同类型的文件时。他们会被保存到不同的路径。

| 布局 | 路径 |
| --- | --- |
| post | source/_posts |
| page | source |
| draft | source/_drafts |

> 如果你不香你的文章被处理，你可以将`Front-Matter`中的`layout`设为`false`

## title

Hexo 默认以标题作为文件名，你可以编辑`new_post_name`参数来改变默认的文件名称

## draft

Hexo 的一种特殊布局：`draft`,这种布局在建立时会被保存到`source/_drafts`文件夹，你可以通过`publish`命令将草稿移动到`source/_posts`文件夹。

	$ hexo publish [layout] <title>

草稿默认不会显示在页面中，你可以在执行时加上`--draft`参数，或是把`render_drafts`参数设置为`ture`来预览草稿

## 模版

在新建文章时，Hexo 会根据`scaffolds`文件夹内相对应的文件来建立文件。

	$ hexo new photomd photo

可以在模版中使用的变量

| 变量 | 描述 |
| --- | --- |
| layout | 布局 |
| title | 标题 |
| date | 文件建立日期 |