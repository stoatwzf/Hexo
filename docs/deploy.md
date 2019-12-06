# 一键部署

1\. 安装`hexo-deployer-git`
```
$ yarn add hexo-deployer-git --dev
```
2\. 修改配置`_config.yml`
```
deploy
	type: git
	repo: <repository url>
	branch: [branch]
	message: [message]
```
3\. 一键部署
```
$ hexo clean
$ hexo deploy
```
`deploy`参数配置

| 参数 | 描述 | 默认值 |
| --- | --- | --- |
| repo | 仓库地址（不带`.git`） |
| branch | 部署分支名称 | gh-pages |
| message | 自定义提交信息 | Site updated: {{now('YYYY-MM-DD HH:mm:ss')}} |
| token | 用于通过仓库进行身份验证的可选令牌值 |