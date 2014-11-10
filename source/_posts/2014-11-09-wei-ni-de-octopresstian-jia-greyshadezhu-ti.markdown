---
layout: post
title: "为你的Octopress添加Greyshade主题"
date: 2014-11-09 05:33:26 +0800
comments: true
categories: [octopress]
---
[Greyshade](https://github.com/shashankmehta/greyshade)是一个Octopress的主题由于其简洁的风格深受大家喜爱。  
[这里](https://github.com/shashankmehta/greyshade/wiki/Sites-using-Greyshade/)有一些使用这款主题的blog，包括我也在使用这款主题，下面我就开始教大家如何为Octopress安装这个主题。
<!-- more -->
####为你的blog添加Greyshade主题  
打开Termnial切换到你的octopress目录，依次执行一下命令  
{% codeblock lang:bash %}
git clone git@github.com:shashankmehta/greyshade.git .themes/greyshade //将greyshade checkout 到你的octopress的 .themes目录中  
echo "\$greyshade: color;" //替换'color'为你喜欢的颜色（注意颜色格式是12进制的web颜色例如#2893e3)  
rake "install[greyshade]" //安装 greyshade主题
rake generate 
rake preview 
{% endcodeblock  %}	
	
至此主题安装成功打开浏览器输入localhost:4000就能看到新的主题了 如果想修改Greyshade的一些式样的话可以打开sass目录修改相应的_greyshade.scss文件。
####ps:
1.记得发布到Github哦。  
2.Octopress的式样都放在sass目录下哦。  
3.布局放在source/_layouts下。  
4.由于Octopress是用[jekyllrb](http://jekyllrb.com/)构建的，如果你需要更加详细的定制情参考[这里](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)。

