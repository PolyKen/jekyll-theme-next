---
title: Mechanism Design - Auction Theory
date: 2020-02-04
categories:
- notes
tags: 
- Game Theory
- Mechanism Design
- Auction Theory
---

机制设计(Mechanism Design)是经济学和博弈论中的一个重要问题，在投票、拍卖流程等经济活动的设计中都有大量应用。
一个好的机制，无疑能让制定者获取更多利润，下面将以拍卖为例，介绍机制设计的相关理论。


### 模型

本次讨论的拍卖流程模型将作如下设定：

- 在此次拍卖中，有一个卖家和N个买家，买家全体的集合记为$\mathcal{N}=\lbrace 1,2,\...,N \rbrace$。

- 卖家有一个商品，且商品对卖家的价值为0。

- 每一个买家对于该商品都有一个自己的估值(value)$X_i$，且这个估值服从分布$F_i$，该分布的密度函数记为
$f_i$，支撑为$\mathcal{X}_i=[0, w_i]$。

- 所有买家估值支撑的笛卡尔积记为$\mathcal{X} = \prod_{j=1}^{N} \mathcal{X}_j$。

- 记$$\mathcal{X}_{-i} = \prod_{j\neq i} \mathcal{X}_j$$。

- 定义$f(x)$为关于$x=(x_1,...,x_N)$的联合密度函数，由于各个$X_i$独立同分布，显然有
$$
    f(x) = \prod_{j=1}^N f_j(x_j)
$$，类似可以定义关于$x_{-i}=(x_1,...,x_{i-1}, x_{i+1}, x_N)$的联合密度函数$f_{-i}(x_{-i})$。


### 机制

一个销售机制(selling mechanism)定义为一个三元组$(B, \pi, \mu)$，其中：

- 每一个买家i都有一个信息集(messages, bids or strategies)，记为$\mathcal{B}_i$，它是买家可能向卖家提供的所有信息的集合。

- 分配规则(allocation rule)是一个函数$\pi: \mathcal{B} \to \Delta$，它将所有买家提供的信息映为一个表示分配结果的概率分布。其中$\mathcal{B} = \prod_{j=1}^N \mathcal{B}_j$，$\Delta = \lbrace (p_1, ... p_N) \in \mathbb{R}^N: \sum_i p_i = 1, p_i \geq 0 \text{ for all i} \rbrace$。

- 支付规则(payment rule)是一个函数$\mu: \mathcal{B} \to \mathbb{R}^N$。它的像是一个$N$维向量，表示全体买家的支付金额。

- 在一轮竞拍中，设全体买家的信息向量为$b=(b_1,...b_N) \in \mathcal{B}$，则$\pi_i(b)$就表示第i个买家最终得到该商品的概率，$\mu_i(b)$就表示第i个买家支付的金额。

- 一个机制在所有买家中定义了一个不完全信息博弈，第i个买家的策略函数为
$$
\beta_i: \mathcal{X}_i=[0,w_i] \to \mathcal{B}_i
$$

- $(\pi(\beta(x)), \mu(\beta(x)))$称为机制的结果(Outcome)。

一个策略组合(strategy profile)$\beta(\cdot)$称为机制的一个贝叶斯纳什均衡(Beyasian Nash equilibrium)，如果对任意的$i$和$X_i$，给定其他买家的策略$\beta_{-i}$，$\beta_i(x_i)$都最大化了买家$i$的期望回报。

### 直接机制(Direct Mechanisms)

在对信息集$\mathcal{B}_i$没有做任何限定的情况下，一个机制可能会非常复杂。比如，买家可以向卖家提供报价，也可以向卖家说明其购买的意愿(明确的“买”或“不买”)，或者是提供其他一些形式复杂的信息，这无疑会给讨论带来麻烦。接下来对机制的讨论将限定在一类结构简单的机制上，并且我们将进一步证明：对这一类机制的研究足以涵盖所有情形。

#### 定义

如果一个机制满足$\mathcal{B} = \mathcal{X}$（对任意的i，$\mathcal{B}_i = \mathcal{X}_i$）。因为在这类机制中，每一个买家都被要求直接提供一个数字(报价)，而不是其他形式的信息，所以这种机制被称为“直接机制”。

- 一个直接机制可写为一个二元组$(Q,M)$，其中：

    - $Q: \mathcal{X} \to \Delta$，$Q_i(x)$表示第i个买家得到商品的概率。

    - $M: \mathcal{X} \to \mathbb{R}^N$, $M_i(x)$表示第i个买家支付的金额。

- 在一个直接机制中，如果$\beta(x)=x$(即每一个买家的策略都是诚实地报出自己的估价)是一个贝叶斯纳什均衡，则称该直接机制存在一个真实均衡(truthful equilibrium)。


### 显示原理(Revelation Principle)

给定一个机制$(\mathcal{B}, \pi, \mu)$和它的一个贝叶斯纳什均衡$\beta$，存在一个直接机制$(Q,M)$，满足：

- 该直接机制的输出和原始机制在给定$\beta$下的输出一致。

- 该直接机制存在一个truthful equilibrium。

**证明**：

定义$Q = \pi \circ \beta$，$M = \mu \circ \beta$，则自然有
$(Q(x), M(x)) = (\pi(\beta(x)), \mu(\beta(x)))$，因此两者有相同的结果。

为证明该直接机制存在一个truthful equilibrium，只需验证$\tilde{\beta}(x)=x$是一个贝叶斯纳什均衡：

对第i个买家，设其value为$x_i$，记他的最佳信息为$z^*(x_i)$，其他买家($j \neq i$)的value和message都是$x_j$，则有

$$
\begin{aligned}
    z^*(x_i) &= \mathop{argmax}\limits_{z \in \mathcal{X}_i}{\lbrace Q_i(z, x_{-i})x_i - M(z, x_{-i})\rbrace}\\
    &= \mathop{argmax}\limits_{z \in \mathcal{X}_i}{\lbrace \pi_i(\beta(z, x_{-i}))x_i - \mu_i(\beta (z, x_{-i}))\rbrace}
\end{aligned}
$$

由于$\beta$是机制$(\mathcal{B}, \pi, \mu)$的贝叶斯纳什均衡，因此

$$
\begin{aligned}
    \mathop{argmax}\limits_{z \in \mathcal{X}_i}{\lbrace\pi_i(\beta(z, x_{-i}))x_i - \mu_i(\beta (z, x_{-i}))\rbrace} = x_i
\end{aligned}
$$

从而有$z^*(x_i)=x_i$。因此$\tilde{\beta}(x)=x$是该直接机制的一个贝叶斯纳什均衡。 **Q.E.D.**

- 显示原理表明，任给一个机制及其相应的BNE，都存在一个有truthful equilibrium的直接机制与之对应，且两者的outcome是一致的。所以，今后关于机制的讨论只需限定在直接机制的范围内。

### 激励相容(Incentive Compatibility)

具有truthful equilibrium的直接机制满足：任给一组$x_1,x_2,...,x_N$，对第i个买家而言，说真话的回报都是最大的，即有下式

$$
    Q_i(x_i, x_{-i})x_i - M_i(x_i, x_{-1}) \geq Q_i(z_i, x_{-i})x_i - M_i(z_i, x_{-i})
$$

对任意的$z_i \in \mathcal{X}_i$都成立。

这是一个很强的条件，我们常常只需要上式在期望的意义下成立。下面引入两个记号：

给定一个直接机制$(Q, M)$，

$$
    q_i(z_i) = \int_{\mathcal{X}_{-i}}Q_i(z_i, x_{-i})f_{-i}(x_{-i})dx_{-i}
$$

表示在第i个买家报价$z_i$且其他买家都报出自己的真实估价的情况下第i个买家获得商品的概率。

类似地，

$$
    m_i(z_i) = \int_{\mathcal{X}_{-i}}M_i(z_i, x_{-i})f_{-i}(x_{-i})dx_{-i}
$$

表示同样情形下第i个买家支付金额的期望。

- 因此，该情形下第i个买家的期望回报可记为：

$$
    q_i(z_i)x_i - m_i(z_i)
$$

#### 定义

给定一个直接机制$(Q,M)$，如果满足对任意的$i,x_i \in \mathcal{X}_i,z_i \in \mathcal{X}_i$，总有

$$
    q_i(x_i)x_i - m_i(x_i) \geq q_i(z_i)x_i - m_i(z_i)
$$

则称该机制为激励相容(Incentive compatible, IC)的。

- 记$V_i(x_i) = \mathop{max}\limits_{z_i \in \mathcal{X}_i} \lbrace q_i(z_i)x_i - m_i(z_i)\rbrace$，
$V_i(x_i)$又称为第i个买家的equilibrium payoff function。

- 记$U_i(x_i) = q_i(x_i)x_i - m_i(x_i)$，$U_i(x_i)$为说真话的情况下第i个买家的期望回报。

#### 性质

1) IC与下面的命题等价：对任意$x_i,z_i$，有

$$
    U_i(z_i) \geq U_i(x_i) + q_i(x_i)(z_i-x_i)
$$

**证明**：

注意到

$$
\begin{aligned}
    q_i(x_i)z_i - m_i(x_i) &= q_i(x_i)x_i - m_i(x_i) + q_i(x_i)z_i - q_i(x_i)x_i\\
    &= U_i(x_i) + q_i(x_i)(z_i - x_i)
\end{aligned}
$$

等式左边$\leq q_i(z_i)z_i - m_i(z_i) = U_i(z_i)$当且仅当IC成立。 **Q.E.D.**

2) U_i逐点可微，且$U_i'(x_i) = q_i(x_i)$，$U_i(x_i) = U_i(0) + \int_0^{x_i}q_i(t)dt$

3) 由于$U_i$是凸函数，因此$q_i$是单调不减的。进一步，$q_i$单调不减等价于IC。


### 收益等价(Revenue Equivalence)

#### 定理

如果一个直接机制是IC的，则对任意的i和$x_i$，第i个买家期望的支付金额为

$$
\begin{aligned}
    m_i(x_i) &= q_i(x_i)x_i - U_i(xi)\\
    &= m_i(0) + q_i(x_i)x_i - \int_0^{x_i}q_i(t)dt
\end{aligned}
$$

这表明，任意两个具有相同分配函数Q的IC机制在相差一个常数的意义下具有相同的期望支付金额。
换言之，如果两个IC机制满足：1）在给定values$(x_1,...,x_N)$的情况下，分配给买家的概率分布相同；2）当value为0时，两个机制的期望支付金额相同。那么对于卖家来说，两种机制的期望收益是一样的。

### 个体理性(Individual Rationality)

- 卖家不能强迫买家参与拍卖。

- 如果买家不参与拍卖，那么他一定不会获得商品，同时他的支出也是0(因而回报也为0)。

#### 定义

如果一个直接机制满足对任意的i和$x_i$，都有$U_i(x_i) \geq 0$，则称这个机制是individually rational(IR)的。

- 如果该机制是IC的，那该机制是IR的等价于$U_i(0) \geq 0$，进而等价于$m_i(0) \leq 0$。

### 最优机制

- 我们的目标是在所有IC、IR的机制中找到收益最高的机制。对于卖家而言，期望收益为：

$$
\begin{aligned}
    E(m_i(\mathcal{X}_i)) &= \int_0^{w_i}m_i(x_i)f_i(x_i)dx_i \\
    &= m_i(0) + \int_0^{w_i}q_i(x_i)x_if_i(x_i)dx_i - \int_0^{w_i} \int_0^{x_i} q_i(t_i)dt_i f_i(x_i)dx_i \\
    &= m_i(0) + \int_0^{w_i}q_i(x_i)x_if_i(x_i)dx_i - \int_0^{w_i} \int_{t_i}^{w_i}q_i(t_i)f_i(x_i)dx_idt_i \\
    &= m_i(0) + \int_0^{w_i}q_i(x_i)x_if_i(x_i)dx_i - \int_0^{w_i} q_i(t_i)[F_i(w_i)-F_i(t_i)]dt_i \\
    &= m_i(0) + \int_0^{w_i}q_i(x_i)x_if_i(x_i)dx_i - \int_0^{w_i} q_i(x_i)[1-F_i(x_i)]dx_i \\
    &= m_i(0) + \int_0^{w_i}(x_i - \frac{1 - F_i(x_i)}{f_i(x_i)})q_i(x_i)f_i(x_i)dx_i \\
    &= m_i(0) + \int_{\mathcal{X}_i}(x_i - \frac{1 - F_i(x_i)}{f_i(x_i)}) \int_{\mathcal{X}_{-i}}Q_i(x_i,x_{-i}) f_{-i}(x_{-i})dx_{-i} f_i(x_i)dx_i \\
    &= m_i(0) + \int_{\mathcal{X}}(x_i - \frac{1 - F_i(x_i)}{f_i(x_i)})Q_i(x)f(x)dx
\end{aligned}
$$

- 最优机制的设计问题可以写为：在满足IC、IR的条件下，最大化$E(m_i(\mathcal{X}_i))$。

- 给定一个估价为$x_i$的买家，定义他的virtual valuation为：

$$
    \Psi_i(x_i) = x_i - \frac{1 - F_i(x_i)}{f_i(x_i)}
$$

- 如果virtual valuation是严格单调递增的，则称这个问题是正则(regular)的。

接下来证明，满足正则性假设时，可以忽略IC、IR的限制条件。

对于卖家而言，他要选取适当的$Q,M$使得下式取最大值

$$
    \sum\limits_{i \in \mathcal{N}}m_i(0) + \int_{\mathcal{X}}(\sum\limits_{i \in \mathcal{N}} \Psi_i(x_i)Q_i(x))f(x)dx
$$