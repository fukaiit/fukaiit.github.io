---
layout:     post
title:      "jekyll文档"
subtitle:   "本文包含jekyll的安装和基本语法，用于复制使用。对于Markdown和Liquid语法单独成文。"
date:       2017-05-04 21:48:06
categories: [movie]
tages:      [jekyll,blog,site]
header-img: "img/post-bg-03.jpg"
---

![jekyll]({{ site.url }}/assets/images/jekyll-logo.jpg)
### 一、安装
* [windows下安装jekyll](http://jingyan.baidu.com/article/925f8cb8f6422ac0dde056ee.html)
* [[环境搭建]Windows下安装Ruby和Jekyll](http://blog.csdn.net/qiujuer/article/details/44620019)
注意：Ruby安装路径不能出现空格

### 二、常用语法
1. include文件：`{% raw %}{% include file.ext %}{% endraw %}`
2. 将content插入页面：`{% raw %}{{ content }}{% endraw %}`
3. `_data`文件夹：Well-formatted site data should be placed here.
4. jekyll默认配置：
	```
	source:      .
	destination: ./_site
	plugins:     ./_plugins
	layouts:     ./_layouts
	include:     ['.htaccess']
	exclude:     []
	keep_files:  ['.git','.svn']
	gems:        []
	timezone:    nil
	encoding:    nil
	
	future:      true
	show_drafts: nil
	limit_posts: 0
	highlighter: pygments
	
	relative_permalinks: true
	
	permalink:     date
	paginate_path: 'page:num'
	paginate:      nil
	
	markdown:      maruku
	markdown_ext:  markdown,mkd,mkdn,md
	textile_ext:   textile
	
	excerpt_separator: "\n\n"
	
	safe:        false
	watch:       false    # deprecated
	server:      false    # deprecated
	host:        0.0.0.0
	port:        4000
	baseurl:     /
	url:         http://localhost:4000
	lsi:         false
	
	maruku:
	  use_tex:    false
	  use_divs:   false
	  png_engine: blahtex
	  png_dir:    images/latex
	  png_url:    /images/latex
	  fenced_code_blocks: true
	
	rdiscount:
	  extensions: []
	
	redcarpet:
	  extensions: []
	
	kramdown:
	  auto_ids: true
	  footnote_nr: 1
	  entity_output: as_char
	  toc_levels: 1..6
	  smart_quotes: lsquo,rsquo,ldquo,rdquo
	  use_coderay: false
	
	  coderay:
	    coderay_wrap: div
	    coderay_line_numbers: inline
	    coderay_line_numbers_start: 1
	    coderay_tab_width: 4
	    coderay_bold_every: 10
	    coderay_css: style
	
	redcloth:
	  hard_breaks: true
	```
5. published: false    表示不需要展示某具体的一遍博文。
6. category和categories：可以用YAML list指定（如 [milk, pumpkin pie, eggs, juice]）或者用空格分开。tags类似。
7. 在头信息中自定义任何变量，都可通过page.XXX调用。
8. 文章列表的基本结构：   
	```html
	{% raw %}<ul>
		{% for post in site.posts %}
			<li>
				<a href="{{ post.url }}">{{ post.title }}</a>
				{{ post.excerpt }}
			</li>
		{% endfor %}
	</ul>{% endraw %}
	```
9. excerpt: 你可以在文章的YAML中增加excerpt来覆盖它。完全禁止掉可以将excerpt_separator设置成""。（`| strip_html` 去掉html标记的文本）
10. 代码高亮 `{% raw %}{% highlight ruby linenos %}{% endraw %}`
11. _drafts : 草稿是没有日期的文章。
12. _data中保存数据  [http://jekyll.com.cn/docs/datafiles/](http://jekyll.com.cn/docs/datafiles/ "Data Files")（取值不成功）
13. 分页功能： [http://jekyll.com.cn/docs/pagination/](http://jekyll.com.cn/docs/pagination/ "分页功能")
14. 使用插件： [http://jekyll.com.cn/docs/plugins/](http://jekyll.com.cn/docs/plugins/ "使用插件")
15. windows下devkit安装： [https://github.com/oneclick/rubyinstaller/wiki/development-kit](https://github.com/oneclick/rubyinstaller/wiki/development-kit)
16. site：_config.yml文件中
	* .time: 跑jekyll命令的时间。
	* .page: pages的清单。
	* .posts： Posts 的清单。
	* .related_posts：10个相关的 Post。
	* .categories.CATEGORY ：所有的在 CATEGORY 类别下的帖子。
	* .tags.TAG：所有的在 CATEGORY 类别下的帖子。
	* .[CONFIGURATION_DATA]：_config.yml 设置的变量。
17. page：YAML头文件信息中
	* .content：
	* .title
	* .excerpt
	* .url
	* .date
	* .id
	* .categories：Categories 是从这个帖子的 _posts 以上 的目录结构中提取的。/work/code/_posts/2008-12-24-closures.md目录下的 Post，这个属性就会被设置成 ['work', 'code']。
	* .tags:
	* .path
	* 任何你自定义的头文件信息都会在 page 中可用。
18. jekyll新增的过滤器
![jekyll新增过滤器]({{ site.url }}/assets/images/newfilter.jpg)  
19. inclued可以传递参数：`{% raw %}{% include footer.html param="value" %}{% endraw %}`  
      调用方法：`{% raw %}{{ include.param }}{% endraw %}`
20. 取得文章链接：
	* `{% raw %}{% post_url 2010-07-21-name-of-post %}{% endraw %}`
	* `{% raw %}[Name of Link]({% post_url 2010-07-21-name-of-post %}){% endraw %}`


### 三、Tips：
1. layouts布局模版的使用定义在YAML头信息中
2. 升级jekyll: gem update jekyll