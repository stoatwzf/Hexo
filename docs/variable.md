# 变量

## 全局变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| site | 网站变量 | object |
| page | 针对该页面的内容及`front-matter`中自定义的变量 | object |
| config | 网站配置 | object |
| theme | 主题配置 | object |
| _ | Loadsh 函数库 | Loadsh 文档 |
| path | 当前页面的路径 | string |
| url | 当前页面的完整网站 | string |
| env | 环境变量 | ??? |

## 网站变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| site.posts | 所有文章 | [{}] |
| site.pages | 所有分页 | [{}] |
| site.categories | 所有分类 | object |
| site.tags | 所有标签 | array |

## 页面变量

页面（page）

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.title | 页面标题 | string |
| page.data | 页面建立日期 | `Moment.js`对象 |
| page.updated | 页面更新日期 | `Moment.js`对象 |
| page.comments | 留言是否开启 | boolean |
| page.layout | 布局名称 | string |
| page.content | 页面的完整内容 | string |
| page.excerpt | 页面摘要 | string |
| page.more | 除了页面摘要的其余内容 | string |
| page.source | 页面的原始路径 | string |
| page.full_source | 页面的完整原始路口 | string |
| page.path | 页面网址（不含根路径）| string |
| page.permalink | 页面的完整网址 | string |
| page.prev | 上一个页面 | string \| null |
| page.next | 下一个页面 | string \| null |
| page.raw | 文章的原始内容 | ??? |
| page.photos | 文章的照片（用于相簿）| array |
| page.link | 文章的外部链接（用于链接文章）| string |

文章（post）与 page 相同，但新增以下变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.published | 如果该文章已发布则为`true` | boolean |
| page.categories | 该文章的所有分类 | array or ??? |
| page.tags | 该文章的所有标签 |  array of ??? |

首页（index）

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.per_page | 每页显示的文章数量 | number |
| page.total | 总文章数 | number |
| page.current | 目前页数 | number |
| page.current_url | 目前分页的网址 | string |
| page.posts | 本页文章 | object |
| page.prev | 上一页的页数 | number |
| page.prev_link | 上一页的网址 | string |
| page.next | 下一页的页数 | number |
| page.next_link | 下一页的网址 | string |
| page.path | 当前页面的路径（不包含根目录）| string |

归档（archive）与 index 布局相同，但新增一下变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.archive | 等于`true` | boolean |
| page.year | 年份归档（4位）| number |
| page.month | 月份归档（没有前导零的2位数）| number |

分类（category）与 index 布局相同，但新增以下变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.category | 分类名称 | string |

标签（tag）与 index 布局相同，但新增以下变量

| 变量 | 描述 | 类型 |
| --- | --- | --- |
| page.tag | 标签名称 | string |
