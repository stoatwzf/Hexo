# 将 Hexo 部署到 Github Pages

[travisUrl]: https://travis-ci.com/ 'Travis CI'
[settingUrl]: https://github.com/settings/installations 'Applications settings'
[tokenUrl]: https://github.com/settings/tokens 'token'


1. 新建一个`repository`。如果你希望你的站点能通过`<username>.github.io`域名访问，你的`repository`应该直接命名为`<username>.github.io`
2. 将你的 Hexo 站点文件夹推送到`repository`中。在`.gitignore`文件中忽略`public`目录
3. 将 [Travis CI][travisUrl] 添加到你的`Github`账户中
4. 前往 Github 的 [Applications settings][settingUrl] 配置 Travis CI 权限
5. 前往 Github 的 [新建 Personal Access Token][tokenUrl]，只勾选`repo`的权限并生成一个新的 `Token`
6. 回到 Travis CI，前往你的`repository`的设置页面，在 **Environment Variables** 下新建一个环境变量，**Name** 为 `GH_TOKEN`，**Value** 为刚才你在 Github 生成的 `Token`
7. 在你的 Hexo 站点文件夹中新建一个`.travis.yml`文件
8. 将`.travis.yml`推送到`repository`中。Travis CI 应该会自动开始运行，并将生成的文件推送到同一`repository`下的`gh-pages`分支下
9. 在 Github 中前往你的`repository`的设置页面，修改`Github Pages`的部署分支为`gh-pages`
10. 前往`https://<username>.github.io`访问

`.travis.yml`文件

	sudo: false
	language: node_js
	node_js:
	- 10 # use nodejs v10 LTS
	cache: npm
	branches:
	only:
		- master # build master branch only
	script:
	- hexo generate # generate static files
	deploy:
	provider: pages
	skip-cleanup: true
	github-token: $GH_TOKEN
	keep-history: true
	on:
		branch: master
	local-dir: public

> `<username>.github.io`仓库默认部署`master`分支，且无法修改。可以将网站部署在其他仓库，如：`site`，并修改`_config.yml`配置如下:

	url: https://<username>.github.io/site/
	root: /site/