# 服务器

	$ hexo server -p prot

启动服务，你的网站会在本机 prot(默认4000) 端口下启动。

## 静态模式

在静态模式下，服务器只处理`public`文件夹内的文件，而不会处理文件变动

	$ hexo server -s

## 自定义IP

服务器默认运行在`0.0.0.0`,你可以覆盖默认的`IP`

	$ hexo server -i 192.168.1.1

## Pow

Pow 是一个 Mac 系统上的零配置 Rack 服务器，它也可以作为一个简单易用的静态文件服务器来使用

安装

	$ curl get.pow.cx | sh

设置

在`~/.pow`文件夹建立链接

	$ cd ~/.pow
	$ ln -s /path/to/myapp

你的网站将会在`http://myapp.dev`下运行