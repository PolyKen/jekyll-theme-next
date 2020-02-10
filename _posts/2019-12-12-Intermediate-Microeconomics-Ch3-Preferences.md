---
title: 读书笔记 - Intermediate Microeconomics - Ch3 Preferences
date: 2019-11-05
categories:
- notes
tags: 
- economics
---

上一章关注的问题是如何描述消费者的消费能力/购买力，这一章则讨论如何描述消费者的preference。

### Preferences

消费者面对琳琅满目的商品，可以做出很多种不同的购买方案(即消费束consumption bundle)。在研究如何选择best bundle的过程中，自然可以想到要把preference当成consumption bundles全体集合上的一个关系来考虑，并且这个preference关系应当满足：

- complete，也即要求任意两个不同的consumption bundle在消费者眼中是可比较的；

- reflexive，同一个consumption bundle和自己在preference的意义下是一样的；

- transitive，如果$\vec{x} > \vec{y}$且$\vec{y} > \vec{z}$，则有$\vec{x} > \vec{z}$。这个条件比较特殊，它在实际生活中并非永远成立，但它是best preference存在的前提条件，因而也是必需的。

preference关系可以进一步分为strictly preference(>)和weakly preference($\geq$).

### Indifference curve

针对特定的bundle $\vec{x}$，考虑集合

$$
    \{\vec{y}: \vec{x} \geq \vec{y}\}
$$

这个集合叫做$\vec{x}$的weakly preferred set。其边界(不含坐标轴)称为indifference curve。这个概念有点类似等高线。

### Examples of Preferences

下面介绍几种典型的Preference，它们的indifference curve也具有典型的特征。

#### Perfect Substitutes

如果消费者愿意按照某个固定的比例用商品A交换商品B，那A和B就称为perfect substitutes。这种情况下的indifference curve是一条斜率为负的直线，显然，斜率的绝对值就是这个交换比例。

#### Perfect Complements

如果两个商品A和B必须按照某个固定的比例被同时购买，那么它们就被称为perfect complements。一个典型的例子是左脚的鞋和右脚的鞋，对(正常?)消费者来说，单独多买了一只脚的鞋子没有产生效益。这种情况下的indifference curve是平行于于坐标轴的射线。

#### Bads

Bad的含义是消费者所厌恶的商品(goods)。在某些情况下，为了购买喜欢的goods，我们需要同时购买一些bads。此时的indifference curve是一条斜率为正的曲线。

#### Neutrals

类似的还有一种“中性”的商品Neutral，它既不能为消费者增加效益，也不会减少效益。显然它的indifference curve是平行于坐标轴的直线。

#### Satiation

有的商品既不是越多越好，也不是越少越好，而是在某个特定的数量上达到最大的效益。这种情况下的indifference curve是一条封闭的曲线（可以是圆、椭圆或其他形状）。

### Well-behaved Indifference Curves

上面介绍了一些典型的preference，涵盖了生活中可能会出现的绝大部分情况。但我们研究的范围还要更小一些，下面对商品要进一步做两个更强的假设：

- monotonicity，即越多越好。

- convexity，平均比极端的情况更好：对于给定的$t \in (0,1)$和$\vec{x} \sim \vec{y}$，总有
$$
    t\vec{x} + (1-t)\vec{y} \geq \vec{x}
$$

这也表明比$\vec{x}$更优的bundle集合是一个convex set。有时我们还会在此基础上进一步假设strict convexity，即排除perfect substitutes的情形：
$$
    t\vec{x} + (1-t)\vec{y} > \vec{x}
$$

### The Marginal Rate of Substitution

indifference curve的斜率（导数）又称为marginal rate of substitution(MRS)。它表示消费者愿意用（极少量的）另一种商品替换（极少量的）这种商品的交换数量比。