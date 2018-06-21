--- 
layout: post
title: Translate "The Algorithmic Foundations of Differential Privacy"
description: Chapter3/Section1 
date: 2018-06-18 
author: ShixiongMarryMe  
link: 
comments: true
photos:
    -
categories:
    - Differential Privacy
tags: 
    - Translation
--- 

>Author: &#160;&#160;&#160;&#160;&#160;&#160;@Cynthia Dwork &#160;&#160;@Aaron Roth
>
>Translator: @ShixiongMarryMe

## 3 基本技术和组合定理

在回顾了一些概率工具之后，我们介绍了拉普拉斯机制，该机制为实值（向量）值查询提供差分隐私。这种应用自然会导致指数机制，这是一种从离散的候选输出集中进行差分隐私选择的方法。然后，我们分析由多个不同私有机制的构成所引起的累积隐私损失。最后，我们给出一种方法：“稀疏矢量技术”@师兄嫁我，用于私下报告潜在的大量计算的结果，前提是只有少数是“显著的”。

在本节中，我们将介绍差分隐私中的一些最基本的技术，我们将再次反复使用这些技术。 这里描述的技术将是我们开发所有其他算法的基本构建块。

### 3.1 有用的概率工具

以下所关注的不等式将会常常被用到。我们以易于使用的形式陈述它们，而非其最完备的形式。

**定理3.1**（加法切尔诺夫界）。 X<sub>1</sub>，...，X<sub>m</sub>是独立的随机变量，其有界性使得对于所有的 i，有0≤X<sub>i</sub>≤1。 令

![3.1.png](https://i.loli.net/2018/06/18/5b274eb19d5b5.png)

表示它们的均值，令μ= E [S]表示它们的预期均值。 然后：

Pr[S > μ + ε] ≤ e<sup>−2mε<sup>2</sup></sup>

Pr[S < μ− ε] ≤ e<sup>−2mε<sup>2</sup></sup>

**定理3.2**（乘性切尔诺夫边界）。 X<sub>1</sub>，...，X<sub>m</sub>是独立的随机变量，其有界性使得对于所有的 i，有0≤X<sub>i</sub>≤1。 令

![3.1.png](https://i.loli.net/2018/06/18/5b274eb19d5b5.png)

表示它们的均值，令μ= E [S]表示它们的预期均值。 然后：

Pr[S > (1+ε)μ ] ≤ e<sup>−μmε<sup>2</sup></sup>/3

Pr[S < (1-ε)μ ] ≤ e<sup>−μmε<sup>2</sup></sup>/3（注：原文为/2，疑误。）

当我们没有独立的随机变量时，所有的都不会丢失 _（all is not lost.附原句）_。我们仍然可以应用Azuma-Hoeffding的不等式：

**定理3.3**（Azuma's 不等式）。 设f是m个随机变量X1，...，Xm的函数，每个Xi从一组Ai取值使得E [f]有界。 令ci表示Xi对f的最大影响，即对于所有ai，a'i∈Ai：

![3.3.png](https://i.loli.net/2018/06/18/5b27568e21014.png)

**定理3.4**（斯特林逼近）。N！可以由<img src="http://latex.codecogs.com/gif.latex?\sqrt{2n\pi&space;}(n/e)^{n}"/>近似为：

![3.4.png](https://i.loli.net/2018/06/18/5b2757c87df44.png)

---
今天端午节哎，想吃个粽子呢Ψ(￣∀￣)Ψ。

&nbsp;

> <span style="color:orange"> To see more, please visit [<span style="color:blue">Homepage</span>](https://ShixiongMarryMe.github.io/). </span>

> <span style="color:orange"> Connect with me at <span style="color:blue"><shixiongmarryme@gmail.com></span>. </span>

__*欢迎纠正不妥之处，转载敬请注明出处*__


 	↓ This block just for test Mathematical formula
 $$
 \sqrt{3x-1}+(1+x)^2
 $$

 $$h(\theta)=\sum_{j=0}^n \theta_jx_j$$

 &fnof;(x)=x+1

 &radic;5

30&deg;

z=z_l

\frac{d}{dx}e^{ax}=ae^{ax}\quad \sum_{i=1}^{n}{(X_i - \overline{X})^2}


 	↑ This block just for test Mathematical formula

<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>