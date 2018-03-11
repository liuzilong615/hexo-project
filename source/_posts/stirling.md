---
title: "Stirling 公式"
date: 2018-01-14 18:41:57 +0800
categories: 
  - proof
tags: 
  - math
excerpt: "A proof of Striling formula"
mathjax: true
---

Stirling 公式证明

============

斯特林公式（Stirling's approximation）是一条用来取n的阶乘的近似值的数学公式。一般来说，当n很大的时候，n阶乘的计算量十分大，所以斯特林公式十分好用，而且，即使在n很小的时候，斯特林公式的取值已经十分准确。

斯特林公式描述如下：

$$
\lim_{n\to \infty}{n!} \to \sqrt{2\pi n} (\frac{n}{e})^n
$$

下面对公式做一下证明，考虑对n!取对数，那么$$ln(n!)=\sum_{k=1}^n{ln(k)}$$,它是从1到n的对数直方图的累加，如图：

<div style="text-align:center">
  <img width="450" height="200" src="/assets/images/stirling/ln_x_histogram.png"/>
</div>

直觉上用$$\int_1^n{ln(x)}dx$$可以逼近直方图的累计和，因为对数函数为凹函数，对曲线分别做内接和外切线，可以得到积分面积的一个上下限：

<div style="text-align:center">
  <img width="450" height="200" src="/assets/images/stirling/ln_x_lower.png"/>
  <div style="text-align:center">内接梯形为下限累计值</div>
</div>

<div style="text-align:center">
  <img width="450" height="200" src="/assets/images/stirling/ln_x_upper.png"/>
  <div style="text-align:center">外切梯形为上限累计值</div>
</div>

于是就有不等式：

$$
\sum_{k=1}^{n-1}{ \frac{\ln k + \ln (k+1)}{2} } 
\leq \int_1^n{ln(x)}dx 
\leq \sum_{2}^{n-1}{\ln k} + \frac {\ln n}{2} + \frac {1}{4}
$$

整理之后：

$$
\sum_{k=1}^{n}{\ln k} - \frac {\ln k}{2}
\leq n \ln n - n + 1
\leq \sum_{k=1}^{n}{\ln k} - \frac {\ln n}{2} + \frac {1}{4}
$$

$$
0 \leq \sum_{k=1}^{n}{\ln k} - (n+ \frac{1}{2})\ln (\frac {n}{e}) - \frac {5}{4} \leq \frac {1}{4}
$$

令$$s_{n}=\sum_{k=1}^{n}{\ln k} - (n+ \frac{1}{2})\ln (\frac {n}{e}) - \frac {5}{4} $$，那么$$s_{n}$$是一个有界序列，如果它同时也是单调序列，那么序列收敛。有:

$$
s_{n+1} - s_{n} 
= \ln (n+1) - (n+1+ \frac{1}{2})\ln (\frac {n}{e}) + ( n + \frac {1}{2}) \ln (\frac{n}{e})
= 1 - (n+\frac{1}{2})\ln \frac{n+1}{n}
$$

令$$f(t)=\ln(1+t)$$,对f(t)在0附近做[泰勒展开]({{ site.url | append: tylor_post.url }}) , 其中$$f^{(k)}(t)=(-1)^{k-1}\frac {(k-1)!}{(1+t)^{k}}$$：

$$
f(t) = \ln ( 1 + t) = \frac {t}{1+t} - \frac{1}{2} (\frac {t}{1+t})^2 + \frac {1}{3} (\frac{t}{1+t})^3 - \frac {1}{4}(\frac {t}{1+t})^4 ...
\lt \frac {t}{1+t}
$$

于是，求得$$f(\frac {1}{n}) = \ln ( 1 + \frac{1}{n})  \lt \frac{1}{n+1} $$，因此
$$
s_{n + 1} - s_{n} = 1 - ( n + \frac{1}{2})\ln (1 + \frac{1}{n})
\gt 1 - \frac {n + \frac{1}{2}}{n + 1}
\gt 0
$$
，可知序列单调递增，因此序列收敛并且有上确界，$$s_{n}$$的极限就是此上确界。

$$
\lim_{n \to \infty} s_{n} \to C_0 (C_0 为某个常数)
$$

$$
\lim_{n \to \infty} e^{s_n} \to C_1
$$

继续化简，消除$$s_n$$中的常数部分，可以得到:

$$
\lim_{n \to \infty} \frac {n!}{(\frac{n}{e})^{(n+1/2)}} \to C
$$

最后，需要用到Wallis公式，针对求出的极限，算出常量C，Wallis公式如下所示， 它是根据对三角函数n次方积分，在极限情况下推出，收敛到一个跟$$\frac {\pi}{2}$$相关的数：

$$
\lim_{n \to \infty} \frac {(2n)!!}{(2n + 1)!!} \frac {(2n)!!}{(2n - 1)!!}
\to \frac {\pi}{2}
$$

将Wallis公式稍做变换，并将之前求出的极限式代入，可得到：

$$
\lim_{n \to \infty} \frac {(2n)!!}{(2n + 1)!!} \frac {(2n)!!}{(2n - 1)!!}
$$

$$
= \lim_{n \to \infty} \frac {2^{4n}(n!)^{4}}{(2n)!(2n)!} \frac {1}{2n+1}
$$

$$
= \lim_{n \to \infty} \frac {(\frac {n}{e})^{4(n+1/2)} 2^{4n}C^4}
{(\frac {2n}{e})^{2(2n + 1/2)} C^{2}} \frac {1}{2n+1}
$$

$$
=\lim_{n \to \infty} {\frac {(\frac {n}{e})C^2}{2(2n+1)}} \to \frac {\pi}{2}
$$

因此$$C = \sqrt{2\pi e}$$，并且
$$
\lim_{n \to \infty} { \frac {n!}{(\frac{n}{e})^{(n+1/2)}} } \to \sqrt{2\pi e}
$$
，于是很容易知道$$\lim_{n\to \infty}{n!} \to \sqrt{2\pi n} (\frac{n}{e})^n   $$了。

> 
> 
> 
<br/>






