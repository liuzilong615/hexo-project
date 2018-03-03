---
title:  "多元泰勒展开"
date:   2018-01-20 16:00:57 +0800
categories: "proof"
tags: math
excerpt: "multivariate tylor series"
mathjax: true
---


多元泰勒公式
===========



>以二元函数为例，对二元函数做泰勒展开，更高元函数类似。假设函数f(x,y)在某个点p的邻域内n阶二元可导，对f(x,y)在$$(x_{0},y_{0})$$附近做泰勒展开。

>首先假设函数f(x,y)只在在某个向量方向上取值,比如向量(h,k),那么在这个方向上，可将多元函数转为一元函数，继而转化为在一元函数上做[泰勒展开]({{ site.url | append: tylor_post.url}})：

$$
x = x(t) = x_{0} + ht
$$

$$
y = y(t) = y_{0} + kt
$$

$$
g(t) = f(x,y) = f(x(t), y(t)) = f(x_{0} + ht, y_{0} + kt)
$$

>对g(t)做泰勒展开，即是f(x,y)的二元展开序列，因此可以先求出g(t)的k阶导数。

$$
g(t) = \frac {\partial f}{\partial x} \frac {dx}{dt} 
+ \frac {\partial f}{\partial y} \frac {dy}{dt}
= (h\frac {\partial}{\partial x} + k \frac {\partial }{\partial y})f_{xy}
$$

>可以推导出

$$
g^{(k)}(t) = (h\frac {\partial}{\partial x} + k \frac {\partial }{\partial y})^{k}f_{xy}
$$

>其中$$(h\frac {\partial}{\partial x} + k \frac {\partial }{\partial y})$$为算子,可直接按照多项式计算,因此，直接带入一维泰勒展开式，就得到令二维展开

$$
f(x,y) = \sum_{k=0}^{n-1} \frac {((x-x_{0})\frac {\partial}{\partial x} + (y-y_{0}) \frac {\partial }{\partial y})^{k}f_{x_{0}y_{0}}}{k!} + \frac {((x-x_{0}) \frac {\partial}{\partial x} + (y-y_{0}) \frac {\partial }{\partial y})^{n}f_{x_{\xi}y_{\xi}}}{n!}
$$

>其中$$(x_{\xi}, y_{\xi})$$在$$(x_{0}, y_{0})$$和$$(x,y)$$之间。


<br/>













