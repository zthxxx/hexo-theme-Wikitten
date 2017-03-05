# hexo-theme-Wikitten

[English Page](./README.md)

### 一个仿 [Wikitten](https://wikitten.vizuina.com/) 样式的 Hexo 个人 wiki 系统主题。 >[预览](http://wiki.zthxxx.me/)

![Site Preview](./source/images/SitePreview.png)

适用于个人 wiki 知识管理。简洁，双栏，分类管理。将知识多级分类整理，侧边可展开各级分类，方便联想跳转。

## 安装说明

`hexo-theme-Wikitten` 核心功能代码基于 [icarus](https://github.com/ppoffice/hexo-theme-icarus)，所以你可以在 [icarus wiki](https://github.com/ppoffice/hexo-theme-icarus/wiki) 阅读基础功能文档。

### 安装

**Wikitten 主题需要 Hexo v3.0 及以上版本。**

```bash
$ cd your-hexo-directory
$ git clone https://github.com/zthxxx/hexo-theme-Wikitten.git themes/Wikitten
$ cp themes/Wikitten/_source/* source/
$ cp themes/Wikitten/_scaffolds/* scaffolds/
```

**需要安装的插件写在主题的 `package.json` 文件中。**

```json
"hexo-autonofollow": "^1.0.1"	// 打开非本站链接时自动开启新标签页
"hexo-generator-feed": "^1.2.0"	// 生成 RSS 源
"hexo-generator-json-content": "^2.2.0"	// 生成全站文章 json 内容，配合搜索使用
"hexo-generator-sitemap": "^1.1.2"	// 生成全站 sitemap
"hexo-renderer-mathjax": "^0.6.0"	// 渲染 LaTex 公式
```

你可以将这些插件合并到**站点**的 `package.json` 文件中通过 `npm install` 一次安装，

或者在**站点目录**下，你可以通过以下命令安装他们：

```bash
$ npm install -s hexo-autonofollow
$ npm install -s hexo-generator-feed
$ npm install -s hexo-generator-json-content
$ npm install -s hexo-generator-sitemap
$ npm install -s hexo-renderer-mathjax
```

### 启用

修改站点 `_config.yml` 文件中的 `theme` 选项为 **`Wikitten`**。

### 更新

```bash
$ cd themes/Wikitten
$ git pull origin master
```



## 配置说明

在站点配置文件 `_config.yml` 中， **推荐配置为**：

```yaml
# Hexo Configuration
# URL
permalink: wiki/:title/

# Directory
skip_render:
  - README.md
  - '_posts/**/embed_page/**'

# Writing
new_post_name: :title.md # File name of new posts

## Markdown
## https://github.com/hexojs/hexo-renderer-marked
marked:
  gfm: true
  
## Plugins: https://hexo.io/plugins/
### JsonContent
jsonContent:
  meta: false
  pages:
    title: true
    date: true
    path: true
    text: true
    tags: true
    categories: true
  posts:
    title: true
    date: true
    path: true
    text: true
    tags: true
    categories: true
  ignore:
    - 404.html
    
### Creat sitemap
sitemap:
  path: sitemap.xml

### Adds nofollow attribute to all external links in your hexo blog posts automatically.
nofollow:
  enable: true
  exclude:
    - <your site url domain> # eg: zthxxx.me
```

在**主题**配置文件 `Wikitten/_config.yml` 中，你能阅读到各个选项更多的细节配置。

### `profile`、`comment`、`Share` 和 `miscellaneous` 项都是 **默认关闭的**！ 

（你任然可以打开那些选项，只是不推荐这样做。）

其他的 **推荐设置为**：

```yaml
# Customize
customize: # 首先修改这项里面的信息为你自己的各项信息
	sidebar: left # 侧边栏的所在位置，默认左边
    category_perExpand: false # 侧边栏里的各个分类是否默认展开
    default_index_file: index.md # 是否指定一篇文章作为首页来代替默认的多篇文章的首页。
    
# Widgets
widgets: # 挂件，默认指开启了分类这一栏
    - category
    # - recent_posts
    # - archive
    # - tag
    # - tagcloud
    # - links
    
# History version 
history_control: # 启用这一项使得 wiki 能有历史版本的功能（查看源码、在线编辑、对比历史变动）
    enable: true
    server_link: https://github.com # 版本控制服务器，推荐使用 GitHub https://github.com
    user: <your GitHub name>
    repertory: <your repertory name of this wiki source code>
    branch: <branch name of this wiki site source code>
```



## 版权协议

[MIT LICENSE](./LICENSE)



