---
title: 序理论基础
teaser: 序理论的基本概念介绍
category: 介绍篇
tags: [计算机科学]
---

# 偏序集

## 二元关系

两个集合 $$M , N$$ 上的 二元关系 $$R$$，即 $$M\times N$$ 的子集。
> 如果 $$ N = M $$，则称为 **集合 $$M$$ 上的关系 $$R$$**

$$(m, n) \in R$$ ，也可以写为 $$m R n$$

$$R^{-1}$$ 称为 $$R$$ 的逆关系。

$$n R^{-1} m :\Leftrightarrow m R n$$

## 偏序关系

集合 $$M$$ 上的关系 $$R$$ ，如果对于所有元素 $$x, y, z \in M$$ 满足以下条件：
1. 自反性：$$x R x$$
2. 反对称性：$$x R y \wedge x \neq y \Rightarrow \neg y R x$$
3. 传递性：$$x R y \wedge y R z \Rightarrow x R z$$

偏序关系 $$R$$ 记为 $$\leq$$，而 $$R^{-1}$$ 则记为 $$\geq$$。

$$x < y :\Leftrightarrow x \leq y \wedge x \neq y$$

偏序集写作 $$(M, \leq)$$，其中 $$\leq$$ 为 $$M$$ 上的偏序关系。

## 近邻

如果 $$a < b$$ 且不存在 $$c$$ 满足 $$a < c < b$$，则称 $$a$$ 为 $$b$$ 的**下近邻**，写作 $$a \prec b$$。而称 $$b$$ 为 $$a$$ 的**上近邻**。

> **Hesse 图表示偏序集 $$(M, \leq)$$.** $$M$$ 中的元素在 Hesse 图中用 **小圆圈** 表示。如果 $$x, y\in M$$ 且 $$x \prec y$$，则 $$y$$ 的圆圈在 $$x$$ 的圆圈之上。


## 可比的、链、宽度和长度
1. 对于偏序集 $$(M, \leq)$$ 的两个元素 $$x, y$$，如果有 $$x \leq y$$ 或 $$y \leq x$$，则称 $$x, y$$ 是可比的，否则称为不可比的；
2. 如果偏序集 $$(M, \leq)$$ 的子集 $$(N, \leq)$$ 中的任意两个元素都是可比的，则该子集称为链；如果任意两个元素都是不可比的，则该子集称为反链。
3. 有限偏序集的宽度定义为其最大反链的大小，无限偏序集的宽度定义为其上确界反链的大小；类似地，长度定义为其上确界链接集的大小减去1。

## 区间、主理想和主滤子
$$a, b, c, d$$ 是偏序集 $$(M, \leq)$$ 的元素，其中 $$b\leq c$$
1. $$[b, c] := \{x\in M \mid b\leq x\leq c\}$$ 称为 **区间**；
2. $$(a] := \{x\in M\mid x\leq a\}$$ 称为 **主理想**；
3. $$[d) := \{x\in M\mid d\leq x\}$$ 称为 **主滤子**。

## 保序、序嵌入和序同构
给定两个偏序集 $$(M, \leq)$$ 和 $$(N, \leq)$$ ，定义映射 $$\phi: M \to N$$。
1. 如果 $$\forall x, y \in M$$ 都有 $$x \leq y \Rightarrow \phi(x)\leq\phi(y)$$，则称 $$\phi$$ 是保序的；
2. 如果 $$\forall x, y \in M$$ 都有 $$x \leq y \Leftrightarrow \phi(x)\leq\phi(y)$$，则称 $$\phi$$ 是序嵌入的；
3. 如果 $$\phi$$ 是序嵌入，且满足双射，则 $$\phi$$ 是序同构的。

注意，双射的保序映射不一定是序同构映射。

## 直接积

给定两个偏序集 $$(M_1, \leq)$$ 和 $$(M_2, \leq)$$，定义偏序集 $$(M_1 \times M_2, \leq)$$，这里 $$M_1 \times M_2$$ 的 $$\leq$$ 定义如下：

$$(x_1, x_2) \leq (y_1, y_2) :\Leftrightarrow x_1\leq y_1 \wedge x_2\leq y_2,$$

$$x_1, y_1 \in M_1, x_2, y_2 \in M_2$$

将该定义推广到多个偏序集：如果 $$T$$ 是一个索引集，而且 $$(M_t, \leq)$$ 是偏序集 $$(t\in T)$$，则 

$$\underset{t\in T}{\times} (M_t, \leq) := (\underset{t\in T}{\times} M_t, \leq)$$

那么

$$(x_t)_{t\in T} \leq (y_t)_{t\in T} : \Leftrightarrow \forall t\in T. x_t \leq y_t$$

## 基本和 (不相交并)

引入符号

$$\dot{M}_t := \{t\}\times M_t$$

定义

$$(M_1, \leq) + (M_2, \leq) := (\dot{M}_1\cup\dot{M}_2, \leq)$$

其中

$$(s, a) \leq (t, b) :\Leftrightarrow s = t \wedge a \leq b$$

该定义也可以推广到多偏序集的情形。

## 偏序集的对偶原理

对于互相对偶的两个命题，只证明其中一个即可，另一个根据对偶原理也成立。

## 下界、上界、下确界 (交)、上确界 (并)
给定偏序集 $$(M, \leq)$$，其中 $$A \subseteq M$$.
1. $$s \in M$$. 满足 $$\forall a \in A. s \leq a$$，则 $$s$$ 为 $$A$$ 的下界；对偶地，得到上界的定义。
2. $$A$$ 的下确界 $$inf A := max\{s \in M\mid\forall a\in A. a\leq s\}$$ 或记为 $$\bigwedge A$$ (经常称为 $$A$$ 的交)；
对偶地，$$A$$ 的上确界 $$sup A := min\{s \in M\mid\forall a\in A. a\geq s\}$$ 或记为 $$\bigvee A$$ (经常称作 $$A$$ 的并)。


# 完全格

## 格、完全格、单位元、零元

> 若对于一个偏序集的每个子集的下确界都存在，则它是完全格。

## 上确界不可约的、下确界不可约的

> 命题2

## 上确界子半格、下确界子半格、完全子格

## 保上确界、完全格同态

<!-- # 闭包算子

# 伽罗瓦连接

定义两个偏序集$$(P, \leq)$$ 和 $$(Q, \leq)$$ 上的映射 $$\phi$$ 和 $$\psi$$。

$$\phi : P \to Q$$ 和 $$\psi: Q \to P$$

如果满足
1. $$p_1 \leq p_2 \Rightarrow \phi p_1 \geq \phi p_2$$
2. $$q_1 \leq q_2 \Rightarrow \psi q_1 \geq \psi q_2$$
3. $$p \leq\psi\phi p$$ 和 $$q \leq\phi\psi q$$

则此映射对 $$(\phi, \psi)$$ 称为伽罗瓦连接。或称这两个映射互为对偶伴随。 -->


*[偏序集]: ordered sets, partially ordered sets
^
*[二元关系]: binary relation
^
*[逆关系]: inverse relation
^
*[偏序关系]: order relation
^
*[Hesse 图]: Hesse diagram, line diagram
^
*[近邻]: neighbour
^
*[下近邻]: lower neighbour
^
*[上近邻]: upper neighbour
^
*[可比的]: comparable
^
*[不可比的]: incomparable
^
*[链]: chain
^
*[反链]: antichain
^
*[宽度]: width
^
*[长度]: length
^
*[区间]: interval
^
*[主理想]: principal ideal
^
*[主滤子]: principal filter
^
*[保序]: order-preserving
^
*[序嵌入]: order-embedding
^
*[序同构]: (order-) isomorphism
^
*[直接积]: (direct) product
^
*[下界]: lower bound
^
*[下确界]: infimum
^
*[交]: meet
^
*[上界]: upper bound
^
*[上确界]: supremum
^
*[并]: join




*[完全格]: complete lattices

<!-- *[伽罗瓦连接]: Galois connection

*[对偶伴随]: dually adjoint -->
