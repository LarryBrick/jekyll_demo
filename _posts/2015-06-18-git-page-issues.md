---
layout: post
tags:   git-page 建站
date:   2015-06-18 21:52
title:  本网站建设中所遇到到的问题及解决方法
published: true
---

　　对于一个初级网站创建者来说，创建网站还是有一定难处的，虽说git-page已经提供了一个很好的平台，但还是不可避免的会遇到很多意想不到的问题，鉴于网上有关git-page建站的内容比较少，自己做些记录方便以后查询，下面记录这期间所遇到的问题，并且不断的更新问题和解决方法.

[TOC]

<!-- more -->


### **首页显示摘要问题**

**问题:**每篇博客在主页上有个摘要的显示能够更好的辅助标题进行了解博客的内容，模板默认的摘要都是第一段，这是因为jekyll默认将摘要分割标识：`excerpt_separator`设置了换行，但是有些时候我们的博文可能是从其他位置拷贝过来，这样的换行可能就不是utf-8，摘要分割标识就无法找到换行标识来截取第一段。

查找[官网](http://jekyllrb.com/docs/posts/)我们可以看到这样的例程:

	---
	excerpt_separator: <!-- more -->
	---
	Excerpt
	<!-- more -->
	out-of-excerpt

> You can also set the excerpt_separator globally in your _config.yml configuration file.

翻译一些：如果你不想使用自动产生的blog摘要，你可以在blog的YAML中添加摘要分割标识来覆盖原来的机制。这里你可以在blog的YAML中定义一个`excerpt_separator`标签。

你也可以在_config.yml配置文件中进行这样的定义。

这样我们就很清楚的知道，只要在_config.yml文件中或者在blog.md文件的头部添加`excerpt_separator`标签，然后博文中在摘要结束之后添加上标签的内容就可以完美的支持摘要的摘取功能，完全自定义化。

### **博文中显示HTML代码问题**

查看官网中有关代码的引用部分，所说的都是采用TAB缩进进行代码引用，而同样采用TAB缩进引用（显示）HTML代码时会发现HTML代码会直接执行，这个问题有待于解决。
