# hexo-theme-Wikitten

[中文版文档](./README_zh-CN.md)

### A personal wiki imitate [Wikitten](https://wikitten.vizuina.com/) style for Hexo. >[Preview](http://wiki.zthxxx.me/)

some features:

- Applicable to personal wiki knowledge management
- Simple, double column, classified management
- The knowledge of multi-level sorting, the side can be expand at all levels of classification, easy to jump
- Categorize article according to file directory  #4

![Site Preview](./source/images/SitePreview.png)



![mobile preview](./source/images/mobile1.png) ![mobile preview](./source/images/mobile2.png)



## Installation

`hexo-theme-Wikitten` kernel code base on [icarus](https://github.com/ppoffice/hexo-theme-icarus), so you can read base function document with [icarus wiki](https://github.com/ppoffice/hexo-theme-icarus/wiki).

### Install

**Note: This theme requires Hexo v3.6 or late.**

1. Go to your hexo folder, then clone this theme `Wikitten` into `themes/`

```bash
$ cd your-hexo-directory
$ git clone https://github.com/zthxxx/hexo-theme-Wikitten.git themes/Wikitten
```

2. Rewrite to cover some default page template in site folder

```bash
$ cp -rf themes/Wikitten/_source/* source/
$ cp -rf themes/Wikitten/_scaffolds/* scaffolds/
```

3. Rename the `_config.yml.example` to `_config.yml` so you can config theme

```bash
$ cp -f themes/Wikitten/_config.yml.example themes/Wikitten/_config.yml
# edit and customize it
$ vim themes/Wikitten/_config.yml
```

most configurations are same as the [icarus](https://github.com/ppoffice/hexo-theme-icarus) theme, you can read with [icarus wiki](https://github.com/ppoffice/hexo-theme-icarus/wiki) at first.

some recommend options setting which you can out of the box, see below [#Configuration](#Configuration).

4. Plugins requires in theme [`package.json`](./package.json) and you need install these.

here is those function and effect:

```json
hexo-autonofollow       // automatic make user open external links in new tab
hexo-directory-category // automatic categorize article according to their file directory
hexo-generator-feed     // generate Atom 1.0 or RSS 2.0 feed
hexo-generator-json-content // generate a json content file for site search
hexo-generator-sitemap  // generate sitemap
```

you can merge these plugins into the **site's** `package.json` file by `npm install ` command install them once,

or in the **site folder**, you can install them with the following command:

```bash
$ npm install --save hexo-autonofollow hexo-directory-category hexo-generator-feed hexo-generator-json-content hexo-generator-sitemap
```

5. `mathjax` renderer configuration (optional)：

If you need to write mathematical formulas, the following configuration is recommended:

First, you need to install [pandoc](https://pandoc.org/installing.html)，and modify the rendering engine under the hexo site in the meanwhile:

```bash
$ npm un hexo-renderer-marked --save
$ npm i hexo-rendere-pandoc --save # or hexo-renderer-krammed
```

Modify settings in site config file `_config.yml`:

```bash
math:
  enable: true
  engine: mathjax
```

### Enable

Modify `theme` setting in site config file `_config.yml` to **`Wikitten`**.

### Update

```bash
$ cd themes/Wikitten
$ git pull origin master
```

## Configuration

In site config file `_config.yml`, **recommend settings**:

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

In **theme** config file `Wikitten/_config.yml`, you can read more detailed commentary for some options.

**Before the start, plase first change my personal info to yourself, including options that `profile` `social_links` `history_control` and so on.**

### `profile`, `comment`, `Share` and `miscellaneous` are **DEFAULT DISABLE**! 

(You still can enable them, but not recommend.)

other theme **recommend settings**:

```yaml
# Customize
customize: # modify this information for yourself
    sidebar: left # sidebar position, options: left, right
    category_perExpand: false # enable article categories list per expanding
    default_index_file: index.md # enable this, it will display at site index instead of default index page, or disable that it will display more articles order by time 
    
# Widgets
widgets: # default use category only
    - category
    # - recent_posts
    # - archive
    # - tag
    # - tagcloud
    # - links
    
# History version 
history_control: # make you wiki has history version control in page (view source code, edit online, compare historical changes)
    enable: true
    server_link: https://github.com # recommend use GitHub - https://github.com
    user: <your GitHub name>
    repertory: <your repertory name of this wiki source code>
    branch: <branch name of this wiki site source code>
```



## License

[MIT LICENSE](./LICENSE)



