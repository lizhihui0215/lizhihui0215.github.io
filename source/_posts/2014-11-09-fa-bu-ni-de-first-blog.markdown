---
layout: post
title: "发布你的 First Blog"
date: 2014-11-09 05:37:27 +0800
comments: false
categories: [octopress]
keywords: octopress, 发布博客，发布octopress博客
description: 用octopress 写博客

---
接下来我们可以开始写自己的博客了，依次按照下面的步骤就可以发布自己的blog了。  
<!-- more -->
打开Terminal切换到你的Octopress目录下依次执行一下命令。
{% codeblock lang:rb %}
rake new_post["your blog title"]
{% endcodeblock  %}	
以上命令将会生成一个在source/_posts/
	目录下生成一个xxxx-xx-xx-your-blog-title.markdown的文件,
	'you blog title'将会决定最后生成的URL  
	http://site.com/blog/xxxx/xx/xx/your-blog-title/index.html。
	
打开source/_posts/xxxx-xx-xx-your-blog-title.markdown文件你会看到如下如下内容。
	
	---
	layout: post // layout type
	title: "your blog title" //the title 
	date: 2011-07-03 5:59 //published date
	comments: true //allowed comments
	categories:  //which tag to be beloged
	---
在这个下面就可以写自己的blog 当然你可以用任何你喜欢的编辑器开始写自己的blog。
在这里我推荐你使用[Mou](http://25.io/mou/)他是款支持markdown语法的编辑器你，可以更加方便你写自己的blog。  
[Markdown语法参考](http://wowubuntu.com/markdown/index.html)
####Mou

![image](http://25.io/mou/img/1@2x.png)