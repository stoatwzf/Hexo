# 数据文件

此功能会载入`source/_data`内的`YAML`或`JSON`文件

在`source/_data`文件夹中新建`menu.yml`文件

	Home: /
	Gallery: /gallery/
	Archives: /archives/

在模版中使用

	<% for (var link in site.data.menu) { %>
		<a href="<%= site.data.menu[link] %>"><%= link %</a>
	<% } %>

渲染结果

	<a href="/>Home</a>
	<a href="/gallery/">Gallery</a>
	<a href="/archives">Archives</a>