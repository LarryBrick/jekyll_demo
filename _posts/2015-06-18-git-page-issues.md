---
layout: post
tags:   git-page 建站
date:   2015-06-18 21:52
title:  本网站建设中所遇到到的问题及解决方法
published: true
---

　　对于一个初级网站创建者来说，创建网站还是有一定难处的，虽说git-page已经提供了一个很好的平台，但还是不可避免的会遇到很多意想不到的问题，鉴于网上有关git-page建站的内容比较少，自己做些记录方便以后查询，下面记录这期间所遇到的问题，并且不断的更新问题和解决方法：

<!-- more -->

###首页显示摘要问题

摘要显示：
主页index.html中扫描：
	html
	<ul>
	  {% for post in site.posts %}
	    <li>
	 	  <a href="{{ post.url }}">{{ post.title }}</a>
		    {{ post.excerpt | remove: '<p>' | remove: '</p>' }}
	    </li>
	  {% endfor %}
	</ul>

问题：从网上拷贝一些文字，自己创建文件粘贴进去，这样的blog总是会在首页里显示全文，而我自己创建的blog，手动输入进去文字则只显示第一段，经过不断的删减，最后两个blog网页内容完全一致但还是一个现实全文，一个现实首段，这是个很大的问题。

查找[官网](http://jekyllrb.com/docs/posts/)可以看到:
> If you don’t like the automatically-generated post excerpt, it can be explicitly overridden by adding an excerpt value to your post’s YAML Front Matter.Alternatively, you can choose to define a custom `excerpt_separator` in the post’s YAML front matter. 
```html
	---
	excerpt_separator: <!--more-->
	---
	
	Excerpt
	<!--more-->
	Out-of-excerpt
> You can also set the excerpt_separator globally in your _config.yml configuration file.

> 如果你不想使用自动产生的blog摘要，你可以在blog的YAML中添加摘要分割标识来覆盖原来的机制。这里你可以在blog的YAML中定义一个`excerpt_separator`标签如下：
```html
	---
	excerpt_separator: <!-- more -->
	---

	excerpt
	<!-- more -->
	out-of-excerpt
> 你也可以在_config.yml配置文件中进行这样的定义。
