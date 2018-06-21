--- 
layout: post
title: Translate "The Algorithmic Foundations of Differential Privacy"
description: Chapter3/Section4 
date: 2018-06-21 
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


### 3.4 指数机制

在“最常见的名称”和“最常见的情况”例子中，我们使用拉普拉斯噪声估计了计数的响应（分布为名称或医疗状况）的“效用”，并报告了最大噪声。 在这两个例子中，响应的效用都与生成的噪声值直接相关; 也就是说，名称或条件的流行度可以在相同的尺度上以与噪音幅度相同的单位进行适当测量。

*指数机制*是针对我们希望选择“最佳”响应的情况设计的，但直接向计算出的数量添加噪音可能会完全破坏其价值，例如在以最大化收入为目标的拍卖中设定价格，如果向最优价格添加少量正面噪音（以保护投标的隐私）可能会大大降低所得收益。

**例3.5**（南瓜）。 假设我们有充足的南瓜和四个出价人：A，F，I，K，其中A，F，I各出价1.00美元，K出价3.01美元。什么是最优价格？ 在3.01美元的收入是3.01美元，在3.00美元和1.00美元的收入是3.00美元，但在3.02美元的收入为零！

指数机制是用任意实用工具（以及任意非数字范围）回答查询的自然构建块，同时保留了差分隐私。给定一些任意范围R，指数机制是根据一些效用函数定义的：N<sup>|X|</sup>×R→R，它将数据库/输出对映射到效用得分。直观地说，对于一个固定的数据库x，用户更喜欢该机制输出具有最大可能效用分数的R的一些元素。请注意，当我们谈论效用得分u：N<sup>|X|</sup>×R→R的敏感性时，我们只关心u相对于它的数据库参数的敏感性; 它的范围参数可以是任意敏感的：

![1.png](https://i.loli.net/2018/06/21/5b2afad4b5c09.png)

指数机制背后的直觉就是以与exp（εu（x，r）/Δu）成比例的概率输出每个可能的r∈R，因此隐私损失大约为：

![2.png](https://i.loli.net/2018/06/21/5b2afb2f8344b.png)

这种直观的观点忽略了标准化项 _(normalization term 附原词)_ 的一些影响，这些影响由当数据库中的一个额外人员导致某些元素r∈R的效用降低而其他的增加时导致。接下来定义的实际机制为标准化项的变化保留隐私预算的一半。

**定义3.4**（指数机制）。 指数机制M<sub>E</sub>（x，u，R）以与exp（εu（x，r）/2Δu）成比例地概率选择和输出元素r∈R。

指数机制可以定义一个大的任意域上的复数分布，所以在问题的自然参数中，当u的范围是超多项式大时，可能无法有效地实现指数机制。回到南瓜的例子，数据库x上的价格p的效用就是当价格是p，需求曲线如x所描述的时候所获得的利润。潜在价格的范围与实际出价无关，这是非常重要的。否则，在一个数据集中可能存在非零权重的价格，但相邻集合中的权重为零，从而违反差别隐私。

定理3.10。 指数机制满足（ε，0）-差分隐私。

证明。略，后续有空补上，详见原著P38。□

***未完待续。。。***

---

师兄离校倒计时第1天，看着师兄收拾东西，无心学习 ￣へ￣

ヾ(。￣□￣)ﾂ゜゜゜

╭(╯^╰)╮

 ∑(っ °Д °;)っ

━━(￣ー￣*`|||`━━

(づ╥﹏╥)づ

> <span style="color:orange"> To see more, please visit [<span style="color:blue">Homepage</span>](https://ShixiongMarryMe.github.io/). </span>

> <span style="color:orange"> Connect with me at <span style="color:blue"><shixiongmarryme@gmail.com></span>. </span>


__*欢迎纠正不妥之处，转载敬请注明出处*__

[comment]: <> (&nbsp;这是空行)

[//]: <> (&#160;这是空格)

[//]: # (This may be the most platform independent comment)

[^_^]:
    &nbsp;这是空行

[>_<]:
    &#160;这是空格

[>_>]:
    3
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
