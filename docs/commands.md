# 命令

## init

新建一个网站。如果没有设置`folder`,Hexo 默认在目前的文件夹建立网站。

	$ hexo init [folder]

## new

新建一篇文章。如果没有设置`layout`的话。默认使用`_config.yml`中的`default_layout`参数代替。

	$ hexo new [layout] <title>

| 参数 | 描述 |
| --- | --- |
| -p, --path | 自定义新文章的路径 |
| -r, --replace | 如果存在同名文章，将其替换 |
| -s, --slug | 文章的Slug |

## generate

生成静态文件

	$ hexo generate

| 参数 | 描述 |
| --- | --- |
| -d, --deploy | 文件生成后立即部署网站 |
| -w, --watch | 监视文件变动 |
| -b, --bail | 如果发现异常则抛出异常 |
| -f, --force | 强制重新生成文件 |
| -c, --concurrency | 最大同时生成文件数量，默认无限制 |

## publish

发表文档

	$ hexo publish [layout] <filename>

## server

启动服务器

	$ hexo server

| 参数 | 描述 |
| --- | --- |
| -p, --port | 重设端口 |
| -s, --static | 只使用静态文件 |
| -l, --log | 启动日记记录 |

## deploy

部署网站

	$ hexo deploy

| 参数 | 描述 |
| --- | --- |
| -g, --generate | 部署之前预先生成静态文件 |

## render

渲染文件

	$ hexo render <file1>[file2] ...

| 参数 | 描述 |
| --- | --- |
| -o, --output | 设置输出路径 |

## migrate

从其他博客系统迁移内容

	$ hexo migrate <type>

## clean

清除缓存文件和已生成的静态文件

	$ hexo clean

## list

列出网站资料

	$ hexo list <type>