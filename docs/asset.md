# 资源文件夹

资源代表`source`文件夹中除了文章以外的所有文件，例如图片、CSS、JS文件等

如果你的 Hexo 项目中只有少量图片，那么最简单的方法是将它们放在`source/images`文件夹中。

## 文章资源文件夹

修改配置`_config.yml`的`post_asset_folder`参数

	post_asset_folder: true

当资源文件管理功能打开后，Hexo 将会在你每一次通过`hexo new [layout] <title>`命令创建新文章时自动创建一个同名资源文件夹

## 相对路径引用的标签插件

当你打开文章资源文件夹功能后，你就可以使用一下方式引入图片

	{% asset_img example.jpg title %}