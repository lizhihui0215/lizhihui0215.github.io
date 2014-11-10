---
layout: post
title: "利用Github&amp;Octopress搭建自己的个人博客"
date: 2014-11-09 05:19:05 +0800
comments: true
categories: [octopress]
---
你们看到的这个blog 就是基于Octopress和Github搭建而成，我们接下来要做的就是为你搭建一个这样的blog。
<!-- more -->
####note:  
  1. 搭建过程都是基于Mac。  
  2. 系统版本为OX X Yosemite Version 10.10.1(14B17 )
  3. 基于[Octopress](http://octopress.org/)和[Github](https://github.com/)

####用到工具
  1. Terminal 2.5(343)
  2. Ruby 2.0.0p481
  3. Git 1.9.3(Apple Git-50)

####开始搭建
  1. [安装Git](http://git-scm.com/)
  2. [安装Ruby](https://www.ruby-lang.org/en/installation/)
  3. 配置 Octopress  
{% codeblock lang:bash %}
git clone git://github.com/imathis/octopress.git octopres  
cd octopress
{% endcodeblock  %}	
		
  	
####依赖库
{% codeblock lang:rb %}
gem install bundler  
rbenv rehash  
bundle install
{% endcodeblock  %}	
####安装默认主题
{% codeblock lang:rb %}
rake install
{% endcodeblock  %}	
	
	
####本地预览你的博客
{% codeblock lang:rb %}
rake generate  
rake preview
{% endcodeblock  %}	

	 
在浏览器输入localhost:4000就能看到你的博客了。
####配置Github
如果你没有Github账号的话请[注册](https://github.com/join)  
[创建](https://github.com/new)一个 Github Repository Name 为username.github.io 选项全部为默认
####创建Github pages
{% codeblock lang:rb %}
rake setup_github_pages
{% endcodeblock  %}	
  
下面将会提示你输入远程连接的Repository 地址   
	
	git@github.com:yourusername/yourusername.github.io.git
####将Octopress部署到Github上
{% codeblock lang:rb %}
rake generate
rake deploy
git add .
git commit -m ‘your message’
git push origin source
{% endcodeblock  %}	
	
至此所有的配置已经完成，在浏览器输入username.github.com 就可以看到你的博客了。  
####ps:
1.由于没有安装主题所以你看到的是Octopress的一个默认主题  
2.[这里](/issue/deploy/github/issues/index.html)列出了一些常见的问题。
  

