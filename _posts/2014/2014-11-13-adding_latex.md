---
layout: post
title: 在jekyll博客中插入latex公式
categories:
- 技术
tags:
- jekyll 
- latex公式
- 行内公式
- mathjax
---

##stackedit用mathjax在jekyll中插入latex公式
inline: $i \hbar \partial_t \left| \psi \right> = H \left| \psi \right>$

代码：`$i \hbar \partial_t \left| \psi \right> = H \left| \psi \right>$`

default：$$i \hbar \partial_t \left| \psi \right> = H \left| \psi \right>$$

代码：`$$i \hbar \partial_t \left| \psi \right> = H \left| \psi \right>$$`

##如何做到的
一开始百度一下，看到有人推荐mathjax。但是参考了各种文章发现效果都不太好。偶然间发现[stackedit.io](https://stackedit.io)这个网站，是个在线编辑markdown的网站，而且可以直接推送到github上。很nice。

最简单的方式如下：


	<!DOCTYPE html>
	<html>
	<head>
	<title>MathJax TeX Test Page</title>
	<script type="text/x-mathjax-config">
	  MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});
	</script>
	<script type="text/javascript"
	  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
	</script>
	</head>
	<body>
	When $a \ne 0$, there are two solutions to \(ax^2 + bx + c = 0\) and they are
	$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}.$$
	</body>
	</html>


其中


	<script type="text/javascript"
	  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
	</script>

调用了mathjax.js。


	<script type="text/x-mathjax-config">
	  MathJax.Hub.Config({tex2jax: {inlineMath: [['$','$'], ['\\(','\\)']]}});
	</script>

是将另 " \$  \$ " 符号可以用于inline公式的显示。若不加入这段代码，inline 公式的表示是\\(   \\)。（不过我没搞成功，而且stakedit中用的方式是\$\$, 所以我就这样设置了。mathjax没将\$\$设置成默认的行内公式标识符的原因是美国人用它比较多比如：\$100，对于我们没什么影响。。）

##参考资料：
[mathjax官方文档](http://docs.mathjax.org/en/latest/start.html#putting-mathematics-in-a-web-page)
