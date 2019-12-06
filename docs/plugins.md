# 插件

Hexo 有强大的插件系统，是你能轻松扩展功能而不用修改核心模块的源码。在 Hexo 中有两种形式的插件：

脚本（Scripts）

如果你的代码很简单，建议你编写脚本，你只需要把 Javascript 文件放到`scripts`文件夹，在启动时就会自动载入

插件（Packages）

如果你的代码比较复杂，或你想发布到 NPM 上，建议你编写插件。首先在`node_modules`文件夹中建立文件夹，文件夹名称必须以`hexo-`开头

文件夹至少包含2个文件

	.
	├── index.js
	└── package.json

`package.json`中至少要包含`name`,`version`,`main`属性

	package.json
	{
	"name": "hexo-my-plugin",
	"version": "0.0.1",
	"main": "index"
	}