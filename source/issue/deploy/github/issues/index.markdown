---
layout: page
title: "issues"
date: 2014-11-09 05:45
comments: true
sharing: true
footer: true
keywords: octopress
description: sitemap.xml No such file or directory

---
####如果出现：Error: Repository not found
1.[检查你的Repository Name是否正确](https://help.github.com/articles/error-repository-not-found/#check-your-spelling)  
2.[检查Github权限](https://help.github.com/articles/error-repository-not-found/#checking-your-permissions)  
3.[检查ssh key](https://help.github.com/articles/error-repository-not-found/#check-your-ssh-access)  
4.[检查Repository是否存在](https://help.github.com/articles/error-repository-not-found/#check-that-the-repository-really-exists)  
5. 运行 rake generate出现如下错误  
	
	Error reading file /Library/Ruby/Gems/2.0.0/gems/jekyll-sitemap-0.6.1/lib/sitemap.xml: No such file or directory - /Users/lizhihui/octopres/source/Library/Ruby/Gems/2.0.0/gems/jekyll-sitemap-0.6.1/lib/sitemap.xml 
这是jekyll-sitemap 0.6.1的一个bug  在 0.6.2 已经被修复了。  
打开octopres/Gemfile 文件 。
找到 
	
	gem 'jekyll-sitemap' 大概在第八行。  
将其修改为
	
	gem 'jekyll-sitemap', '~> 0.6.2'
