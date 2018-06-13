--- 
layout: post
title: Translate "The Algorithmic Foundations of Differential Privacy"
description: Chapter2/Section3 
date: 2018-05-27 
author: ShixiongMarryMe  
link: 
comments: false
photos:
    -
categories:
    - Differential Privacy
tags: 
    - Translation
--- 

>@Cynthia Dwork
>@Aaron Roth

## 2.3 形式化差分隐私

我们将从差分隐私的技术定义开始，继而对其进行解释。差分隐私将通过一个过程来提供隐私保护。特别是它会引入随机性。随机过程关于隐私的一个早期例子是随机反应，这是一种在社会科学中开发的技术，用于收集关于尴尬或非法行为的统计信息，通过拥有特性*P*来捕获。研究的参与者被告知要报告他们是否拥有如下的特性*P*：

1.翻转一枚硬币。

2.如果是**尾巴**（正面），然后如实回复。

3.如果是**头**（背面），然后翻转第二个硬币，如果是头，则回答“是”，如果是尾，则回答“否”。

 “隐私”来自对任何结果的合理否认；特别是如果把具有特性P等价于从事非法行为的话，即便是一个肯定的回答也没有入罪，因为不管被访者是否实际上具有特性P，这个答案的出现概率至少为1/4。准确性来自于对噪音产生程序的理解(所引入的虚假的“是”和“否”答案来自随机化)：预期的“是”答案的数量是(1/4)\*(没有特性P的参与者的数量)+(3/4)\*(有特性P的参与者数量)。因此，如果小p是具有属性P的参与者的真实数量（ true fraction不会翻译，给出原文），则预期的“是”答案的数量是(1/4)\*(1-p)+(3/4)\*p =(1 /4)+ p / 2。 因此，我们可以将小p估计为回答“是”的数量的两倍再减去1/2，即2((1/4)+ p / 2) - 1/2。

随机化是必不可少的; 更准确地说，无论所有当前或未来的辅助信息来源(包括其他数据库，研究，网站，在线社区，八卦，报纸，政府统计等)都可以使用的任何实用的隐私保障都需要随机化。这是从我们现在简单描述的一个简单的混合论点开始的。假设为了产生矛盾，我们有一个实用的确定性算法。实用性认为存在一个查询和两个数据库，在该查询下产生不同的输出。但一次更改一行，我们发现存在一对不同的数据库，只有一行的值不同，相同的查询产生不同的输出。对手知道正确的数据库是这两个几乎相同的数据库中的一个，但只是知道一个未知行中数据的值。

因此，我们需要讨论随机算法的输入和输出空间。 在整篇专著中，我们使用离散概率空间。 有时我们会将我们的算法描述为连续分布的采样，但这些算法应该始终以适当谨慎的方式离散化为有限精度(参见下面的备注2.1)。通常，具有域A和(离散)范围B的随机化算法将与一个从A到B上概率单纯形的映射（a mapping from A to the probability simplex over B，不会翻译，给出原文）相关联，记为Δ(B)：

**定义2.1**(概率单纯形 Probability Simplex)。 给定一个离散集B，其上的概率单纯形记为Δ(B)，定义为：

![2.1.png](https://i.loli.net/2018/05/28/5b0b655799e74.png)

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

**定义2.2**（随机算法）。 随机化算法M：具有域A和离散范围B的，其映射M：A→Δ(B)。在输入a∈A时，对每个b∈B，算法M以概率(M(a))<sub>b</sub>输出M(a)=b。算法M的概率空间在硬币翻转之上（The probability space is over the coin flips of the algorithm M.不会翻译，附上原文）。

我们将数据库x视为来自所有 χ 的记录集合。通过直方图表示数据库通常很方便：
x∈N<sup>|χ|</sup>，其中每个条目xi表示数据库x中元素的数量，其中i∈ χ （我们稍微滥用记号，用符号N表示包括零在内的所有非负整数的集合）。在这个表示中，两个数据库x和y之间自然度量的距离将是它们的ℓ1距离：

![2.3.png](https://i.loli.net/2018/05/28/5b0c03248f901.png)

两个数据库x和y之间的ℓ1距离是|| x-y ||<sub>1</sub>

请注意，|| x ||<sub>1</sub>是数据库x的大小(即它包含的记录的数量)的度量，并且|| x-y ||<sub>1</sub>是x和y之间有多少记录不同的度量。

数据库也可以由多行(X的元素)或甚至有序的行列表来表示，这里有集合的一种特殊情况，其中的行号成为元素名称的一部分。在这种情况下，数据库之间的距离通常通过汉明距离来衡量，即它们不同的行数。

但是，除非另有说明，否则我们将使用上述的直方图表示法。（但是请注意，即使直方图符号在数学上更方便，在实际实现中，多重集合表示通常会更加简洁）。

我们现在准备好正式定义差分隐私，这将直观地保证随机算法在类似的输入数据库上表现相近。

**定义2.4**(差分隐私)。.如果对所有的S⊆Range(M)和对于所有的x，y∈N|X使得‖x-y‖<sub>1</sub>≤1，那么具有域N|X|的随机化算法M满足(ε,δ)差分隐私：

![2.4.png](https://i.loli.net/2018/05/28/5b0c0558e0e84.png)

其中机制M的概率空间在硬币翻转之上（ the probability space is over the coin flips of the mechanism M. 不会翻译，附上原句）。如果δ= 0，我们说M是ε-差分隐私。

通常我们感兴趣的是δ值小于数据库大小的任何多项式的倒数。特别当δ值大约为1 /‖x‖1时是非常危险的：它们通过发布少量数据库参与者的完整记录来允许“保护隐私” - 正是在第1章中讨论的“少数”哲学。

> <span style="color:orange"> To see more, please visit [<span style="color:blue">Homepage</span>](https://ShixiongMarryMe.github.io/). </span>

> <span style="color:orange"> Connect with me at <span style="color:blue"><shixiongmarryme@gmail.com></span>. </span>

__*欢迎纠正不妥之处，转载敬请注明出处*__
