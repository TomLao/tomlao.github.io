---
layout: post
title: latex写公式笔记
subtitle: 不能一味贴图了，需要动手去写数学表达式
date: 2020-06-07
authro: tomlao
header-img: https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200607122232785.png
catalog: true
tags:
- 笔记
---
论文地址：[http://www.ms.k.u-tokyo.ac.jp/2010/SELF.pdf](http://www.ms.k.u-tokyo.ac.jp/2010/SELF.pdf)
论文ppt：[http://www.ms.k.u-tokyo.ac.jp/2008/PAKDD2008-slides.pdf](http://www.ms.k.u-tokyo.ac.jp/2008/PAKDD2008-slides.pdf)
论文简介及代码：[http://www.ms.k.u-tokyo.ac.jp/software.html](http://www.ms.k.u-tokyo.ac.jp/software.html)

# Fisher linear discriminant analysis总结

1. 线性判别分析是统计学上的一种分析方法，用于在已知的分类之下遇到有新的样本时，选定一个判别标准，以判定如何将新样本放置于哪一个类别之中。主要用于二分类问题，对于多类问题则可以多次运用该方法就可以了；
2. Fisher线性判别分析的主要原理是将带有类别标签的高维样本投影到一个向量w（一维空间）上，使得在该向量上2类样本的投影值达到“低耦合高内聚“，即类内距离最小而累间距离最大，这样便是分类效果最好的情况）这样便可将问题转化成一个确定w的优化问题。
3. 其实w就是二分类问题的超分类面的法向量。
4. 类似于SVM和kernel PCA，也有kernel FDA，其原理是将原样本通过非线性关系映射到高维空间中，在该高纬空间利用FDA算法，这里的关键是w可以用原影本均值的高维投影值表示，这样可以不需知道具体的映射关系而给出kernel的形式就可以了。
5. 和PCA一样，FDA也可以看成是一种特征提取（feature extraction）的方法，即将原来的n维特征变成一维的特征了（针对该分类只要有这一个特征就足够了）。
6. 监督降维方法：包括Fisher判别分析和局部Fisher判别分析，利用样本的类别属性信息进行降维，再有类别属性的样本（标号样本）足够多的情况下，这类算法往往可以取得较好的降维效果。但是再实际应用场合，获取足够多的样本往往是不切实际的。如果仅仅依靠少量标号样本进行降维，当选取的样本没有足够的代表性时，其效果反而不如无监督降维。此时, 综合利用大量无标号样本和少量标号样本的半监督降维方法是一种可行的降维手段。
7. 为了区分不同的数据对对降维的作用，强化样本局部的分布信息，Sugiyama在文献[5]中提出了局部Fisher判别分析法(L-FDA)。L-FDA通过修改式和式逐对系数  和  的定义，使得距离比较远的，具有相同类别属性的数据对(通过)对降维方向的选取产生较小的影响。调节参数  的定义方式有多种，Sugiyama建议采用。实验表明是一个较好地选择。
8. 降维的意义：数据降维是很多模式识别算法的前期准备，合理的降维可以有效降低后期算法的计算量，同时保持模式识别的效果。
9. Fisher Discriminant Analysis(FDA)找最大类间距，最小类内距。有监督学习。
10. Local FDA：
    1. 基本思想：把相邻的同类样本靠近；不管同类但离得远的样本；把不同类的样本分开。
    2. LFDA的标准：扩大局部类间分布，减小局部类内分布。
    3. 方法：局部类内/类间散点矩阵的主特征向量。
    4. 特征：保留了类之间的可分离性质，保留了类内聚类结构，无特征类数上限。
11. 半监督降维的原因：少量带标签样本，大量无标签样本。有监督的降维方法常常对有标签的样本过拟合。我们想要利用上无标签样本。
12. LFDA倾向于过拟合，PCA不使用到样本信息，这两个往往有互补。

![image-20200606221310902](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200606221310902.png)

# Semi-Supervised LFDA(SELF)

半监督的局部Fisher判别分析。

## SELF的基础知识

1. 基本思想：结合LFDA和PCA。
2. 关键事实：都涉及到相似的特征问题。基于特征分解解析计算全局解。![image-20200606221658430](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200606221658430.png)

3. SELF关键：LFDA和PCA的加权和。![image-20200606221940927](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200606221940927.png)
4. 正则化的局部类间散步矩阵：![image-20200606222141837](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200606222141837.png)
5. 正则化的局部类间散步矩阵：![image-20200606222211303](https://gitee.com/tomlao/typoratuchuang/raw/master/img/image-20200606222211303.png)

## SELF的总结：

1. 结合LFDA和PCA的优点。
2. 提高了类间的可分离性。
3. 保留了类内的局部结构。
4. 保留了全局数据结构。
5. 存在封闭式解决方案。
6. 计算快速且稳定。
7. SELF可通过核化法拓展为非线性版。

# 读论文

## 原理

- 当只有少量的标记样本可用时，监督降维方法往往因过度拟合而表现不佳。在这种情况下，未标记的样本可能有助于提高性能。本文提出了一种半监督降维方法，该方法在保持未标记样本的全局结构的同时，将不同类别的标记样本相互分离。本文提出的半监督局部Fisher判别分析（SELF）方法具有全局最优解的解析形式，可以基于特征分解进行计算。通过对基准和真实文档分类数据集的实验，我们证明了SELF的有效性。
- 降维的目的是把高维数据降到低维，同时保留大部分内在信息。
- FDA是流行的有监督学习方法。
- 有监督的LFDA过拟合，无监督的PCA没有利用到标签信息。以无监督的方式保留所有样本的全局结构可能比过多地依赖由少量标记样本提供的类信息要好。
- LFDA和PCA可以弥补各自的不足，即LFDA可以利用标签信息，而PCA可以避免过度拟合。
- 数据的垂直缩放倍增。虽然尺度的这种变化对LFDA和PCA解都有影响，但由于LFDA的监督性质，它不受尺度变化的强烈影响。相比之下，主成分分析受到尺度变化的显著影响，对数据集（c）不起作用。这说明了主成分分析法由于其无监督性而可能存在的弱点。（PCA的缺点：数据尺度垂直放缩后，LFDA影响不大，PCA受尺度变化影响大）

## 公式计算

1. 正则化的局部类间散步矩阵$S^{(rlb)}$，正则化的局部类内散步矩阵$S^{(rlw)}$。要解决广义特征值问题：

$$
S^{(rlb)} \varphi = \lambda S^{(rlw)} \varphi
$$

2. 其中$S^{(rlb)}$和$S^{(rlw)}$的定义为如下。$\beta$为0到1，当$\beta$=1时退化为PCA，当$\beta$=0时退化为LFDA。不同的权衡参数$\beta$增加灵活性，但使得其选取困难。

$$
S^{(rlb)} := (1-\beta)S^{(lb)} + \beta S^{(t)}
\\
S^{(rlw)} := (1-\beta)S^{(lw)} + \beta I_d
$$

3. SELF的优化问题表示为：

$$
T^{(SELF)} := \mathop{argmax}\limits_{T\in R^{d*r}}[tr(T^TS^{(rlb)}T(T^TS^{(rlw)}T)^{-1})]
$$

