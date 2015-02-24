---
layout: post
title: STA General Formalisms(未完)
categories:
- Shortcuts to adiabaticity 学习
tags:
- 量子绝热捷径
- 量子信息
---

我们课题组研究的是量子调控技术。为了日后的研究工作，我需要阅读老师和他合作者一起写的[*这一篇关于量子绝热捷径的综述文章*][2]。这一系列的blog是用来记录我在阅读过程中对综述学习之后的总结。由于刚进入这个领域，难免在理解上会有偏差，错误。在这里记录下来，希望不会贻笑大方。既然说到绝热捷径，那么就有必要先介绍一下什么是绝热过程。

##绝热过程
在量子力学课中，有一章叫做绝热过程（见[*格里菲斯*][1]P368）。这个"绝热过程"，不同于经典力学中的绝热，而是指哈密对量随时间变化地很慢的情况。

举个例子：

我们知道，在量子力学中，系统的性质反应在哈密顿量（$H$）中。对于$H$不随时间改变的系统。我们可以通过求解薛定谔方程（$i \hbar \partial_t \left| \psi \right> = H \left| \psi \right>$）得到系统的演化方式，我们知道：

如果系统一开始处于哈密顿量的本征态 $\left| n \right>$ （其中$\left| n \right>$ 满足：$H \left| n \right> = E_n \left| n \right>$），那么随着时间的推移，系统不会跃迁到其他态上去，只是增加一个相位。系统在 $t$ 时刻的态矢量为：$e^{iEt/ \hbar} \left| n \right>$。

对于哈密顿量随时间改变的系统（$H(t)$）。我们仍然可以通过下式找到 $H(t)$ 的本征态。
$$
	H(t) \left| n(t) \right> = E_n(t) \left| n(t) \right>
$$
但是假设 $t = 0$ 时刻系统处于 $\left| n(0) \right>$ 态，系统状态在演化过程中一般不会一直保持在 $\left| n(t) \right>$ 态上。事实上态的演化方式可以通过求解含时薛定谔方程得到，推导见[*格里菲斯*][1]P372。

然而，当体系的哈密顿量 $H(t)$ 变化地很慢时（即 $\partial_t H(t) \approx 0$），系统的本征态的演化方式可以近似地表示为哈密顿量的瞬时本征态（$\left| n(t) \right>$）。这就是***绝热理论（Adiabatic Theorem）***。

更准确地说：在绝热近似（$\partial_t H(t) \approx 0$）下，如果系统一开始处于 $H(0)$ 的某个瞬时本征态 $\left| n(0) \right>$ 上，系统状态的演化方式近似为
$$e^{i[\theta_n(t) + \gamma_n(t) ] }\left| n(t) \right>$$
其中 $\theta, \gamma$ 是相位，具体推导参考[*格里菲斯*][1]P372。

##What if $\partial_t H(t) \not \approx 0$  
所谓量子调控，就是我们通过对量子系统施加电场，磁场或者别的什么影响，让量子系统按照我们希望的方式演化。



[1]: http://www.amazon.cn/%E6%97%B6%E4%BB%A3%E6%95%99%E8%82%B2%E5%9B%BD%E5%A4%96%E9%AB%98%E6%A0%A1%E4%BC%98%E7%A7%80%E6%95%99%E6%9D%90%E7%B2%BE%E9%80%89%E2%80%A2%E9%87%8F%E5%AD%90%E5%8A%9B%E5%AD%A6%E6%A6%82%E8%AE%BA-%E6%A0%BC%E9%87%8C%E8%8F%B2%E6%80%9D/dp/B001149VXG/ref=pd_bxgy_b_img_z

[2]: http://arxiv.org/abs/1212.6343v1