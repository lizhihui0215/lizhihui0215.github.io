---
layout: post
title: "为你的Octopress加速"
date: 2014-11-09 15:04:25 +0800
comments: true
categories: [octopress]
---

当你在国内打开[Github]()的时候感觉貌似还可以，但是每次打开你的octopress blog貌似每次相当卡。  
用chrome浏览器打开的时候发现左下角每次卡在请求google的字体那一步。  
因此我就打开Finder搜索这个地址，发现在source/_include/head.html 28行中存在如下链接的引用。  
{% codeblock lang:js %}
<link href='http://fonts.googleapis.com/css?family=Nunito:400,300,700' rel='stylesheet' type='text/css'>
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
{% endcodeblock %}  
从这里看出你的问题就我们访问慢的情况就出在对google css 和 js 的引用，（哎，毕竟国内Google被和谐的现在没有VPN根本打不开）。  
因此我们的想法就是吧这两个文件下载到本地直接进行引用，事实证明访问速度得到明显提升。  
OK下面我就开始介绍怎么做。  
1. 新建这个文件夹source/stylesheets/Google-Font/  
2. 浏览器打开[http://fonts.googleapis.com/css?family=Nunito:400,300,700](http://fonts.googleapis.com/css?family=Nunito:400,300,700) ，你会看到如下css  
{% codeblock lang:css %} 
/* latin */
@font-face {
  font-family: 'Nunito';
  font-style: normal;
  font-weight: 300;
  src: local('Nunito-Light'), url(http://fonts.gstatic.com/s/nunito/v7/1TiHc9yag0wq3lDO9cw0voX0hVgzZQUfRDuZrPvH3D8.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215, U+E0FF, U+EFFD, U+F000;
}
/* latin */
@font-face {
  font-family: 'Nunito';
  font-style: normal;
  font-weight: 400;
  src: local('Nunito-Regular'), url(http://fonts.gstatic.com/s/nunito/v7/6TbRXKWJjpj6V2v_WyRbMX-_kf6ByYO6CLYdB4HQE-Y.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215, U+E0FF, U+EFFD, U+F000;
}
/* latin */
@font-face {
  font-family: 'Nunito';
  font-style: normal;
  font-weight: 700;
  src: local('Nunito-Bold'), url(http://fonts.gstatic.com/s/nunito/v7/TttUCfJ272GBgSKaOaD7KoX0hVgzZQUfRDuZrPvH3D8.woff2) format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2212, U+2215, U+E0FF, U+EFFD, U+F000;
}
{% endcodeblock%}  

3.在Google-Font目录下新建一个css文件命名为google-font.css  

	source/stylesheets/Google-Font/google-font.css
4.打开将浏览器打开的内容粘贴到google-font.css中。
	
5.打开Termnail，切换到一个source/stylesheets/Google-Font/目录下执行一下命令。
{% codeblock lang:bash %}
curl -o 1TiHc9yag0wq3lDO9cw0voX0hVgzZQUfRDuZrPvH3D8.ttf 'http://fonts.gstatic.com/s/nunito/v7/1TiHc9yag0wq3lDO9cw0voX0hVgzZQUfRDuZrPvH3D8.woff2'
curl -o 6TbRXKWJjpj6V2v_WyRbMX-_kf6ByYO6CLYdB4HQE-Y.ttf 'http://fonts.gstatic.com/s/nunito/v7/6TbRXKWJjpj6V2v_WyRbMX-_kf6ByYO6CLYdB4HQE-Y.woff2'
curl -o TttUCfJ272GBgSKaOaD7KoX0hVgzZQUfRDuZrPvH3D8.ttf 'http://fonts.gstatic.com/s/nunito/v7/TttUCfJ272GBgSKaOaD7KoX0hVgzZQUfRDuZrPvH3D8.woff2'
{% endcodeblock %} 
以上命令将会在你的source/stylesheets/Google-Font/目录下下载3个google的字体文件。  
6.将google-font.css 中的
	
	url(http://fonts.gstatic.com/s/nunito/v7/1TiHc9yag0wq3lDO9cw0voX0hVgzZQUfRDuZrPvH3D8.woff2) format('woff2');  
	url(http://fonts.gstatic.com/s/nunito/v7/6TbRXKWJjpj6V2v_WyRbMX-_kf6ByYO6CLYdB4HQE-Y.woff2) format('woff2');
	url(http://fonts.gstatic.com/s/nunito/v7/TttUCfJ272GBgSKaOaD7KoX0hVgzZQUfRDuZrPvH3D8.woff2) format('woff2');
分别修改为
	
	url(/stylesheets/Google-Font/1TiHc9yag0wq3lDO9cw0voX0hVgzZQUfRDuZrPvH3D8.ttf) format('truetype')  
	url(/stylesheets/Google-Font/6TbRXKWJjpj6V2v_WyRbMX-_kf6ByYO6CLYdB4HQE-Y.ttf) format('truetype')  
	url(/stylesheets/Google-Font/TttUCfJ272GBgSKaOaD7KoX0hVgzZQUfRDuZrPvH3D8.ttf) format('truetype')
7.用浏览器打开[http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js](http://ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js)  
8.新建source/stylesheets/Google-Font/google-jquery-1.7.2.js文件。  
9.将内容拷贝进google-jquery-1.7.2.js文件将中。  
10.打开source/_includes/head.html找到  
{% codeblock lang:js %}
<link href='http://fonts.googleapis.com/css?family=Nunito:400,300,700' rel='stylesheet' type='text/css'>
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
{% endcodeblock %} 大概在28行左右
将其替换为
{% codeblock lang:js %}
<link href="{{ root_url }}/stylesheets/Google-Font/google-font.css" rel='stylesheet' type='text/css'>
	<script src="{{ root_url }}/stylesheets/Google-Font/google-jquery-1.7.2.js"></script>
{% endcodeblock %}  
11.打开中断运行
{% codeblock lang:bash %}
	rake generate
	rake deploy
{% endcodeblock %}

至此所有的工作都做完了，赶快去打开你的blog 看看是否是飞一般的速度。

####ps:
附上最终创建文件的截图  
![image](http://ww3.sinaimg.cn/bmiddle/a0027cf7gw1em4sesj1b3j20re09mmz1.jpg)



