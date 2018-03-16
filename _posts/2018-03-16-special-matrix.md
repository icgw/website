---
title: 特殊矩阵汇总
teaser: 介绍几类特殊矩阵并归纳
category: 介绍篇
tags: [线性代数]
---

# Vandermonde 矩阵

## 定义

如果矩阵 $$\mathbf{V}$$ 每一行都是从 $$1$$ 开始的等比数列，则称为 Vandermonde 矩阵。

即：

$$\mathbf{V} = \left[\begin{matrix}
1 & \alpha_1 & \alpha_1^2 & \cdots & \alpha_1^{n - 1} \\
1 & \alpha_2 & \alpha_2^2 & \cdots & \alpha_2^{n - 1} \\
1 & \alpha_3 & \alpha_3^2 & \cdots & \alpha_3^{n - 1} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & \alpha_m & \alpha_m^2 & \cdots & \alpha_m^{n - 1} 
\end{matrix}\right].$$

同样地，$$\mathbf{V}^T$$ 也称为 Vandermonder 矩阵。

# Jacobian 矩阵

<!-- Carl Gustav Jacob Jacobi  -->

## 定义
设 $$\mathbf{f}: \mathbb{R}^n\to\mathbb{R}^m$$，如果函数 $$\mathbf{f}$$ 一阶可导，那么 $$\mathbf{f}$$ 的 Jacobian 矩阵 $$\mathbf{J}$$ 为 $$m\times n$$ 矩阵。

定义如下：

$$\mathbf{J} = \left[\begin{matrix}
\frac{\partial\mathbf{f}}{\partial x_1} & \cdots & \frac{\partial\mathbf{f}}{\partial x_n} 
\end{matrix}\right]
= \left[\begin{matrix}
\frac{\partial f_1}{\partial x_1} & \cdots & \frac{\partial f_1}{\partial x_n} \\
\vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x_1} & \cdots & \frac{\partial f_m}{\partial x_n}
\end{matrix}
\right].$$

或分量形式：

$$\mathbf{J}_{i, j} = \frac{\partial f_i}{\partial x_j}.$$

也可以记为 

$$D\mathbf{f}, \mathbf{J}_{\mathbf{f}}\text{ 或 }\frac{\partial(f_1, \dots, f_m)}{\partial(x_1, \dots, x_n)}.$$

# Hessian 矩阵

<!-- 多变量实值函数的二阶偏导数组成的方块矩阵。

它描述了多元函数的局部曲率。

19世纪，德国数学家 Ludwig Otto Hesse 发现。

该矩阵的行列式，也称为 Hessian。 -->

## 定义
设 $$f: \mathbb{R}^n\to\mathbb{R}$$，如果函数 $$f$$ 二阶连续可导，那么 $$f$$ 的 Hessian 矩阵 $$\mathbf{H}$$ 为 $$n\times n$$ 矩阵。

定义如下：

$$\mathbf{H} = \left[\begin{matrix}
\frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1\partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_1\partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \cdots & \frac{\partial^2 f}{\partial x_2\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n\partial x_1} & \frac{\partial^2 f}{\partial x_n\partial x_2} & \cdots & \frac{\partial^2 f}{\partial x_n^2} \\
\end{matrix}\right].$$

或分量形式：

$$\mathbf{H}_{i, j} = \frac{\partial^2 f}{\partial x_i\partial x_j}.$$

也可以记为

$$\mathbf{H}(f(\mathbf{x})) = \mathbf{J}(\nabla f(\mathbf{x}))^T.$$

<!-- ## Hessian 矩阵的应用

当函数 $$f: \mathbb{R}^n\to\mathbb{R}$$ 二阶连续可导时，Hessian 矩阵 $$\mathbf{H}$$ 在临界点 $$x_0$$ 上是一个 $$n\times n$$ 对称矩阵。

* 当 $$\mathbf{H}$$ 是正定矩阵时，临界点 $$x_0$$ 是一个局部的极小值。
* 当 $$\mathbf{H}$$ 是负定矩阵时，临界点 $$x_0$$ 是一个局部的极大值。
* 当 $$\mathbf{H} = 0$$ ，需要更高阶的导数来帮助判断。
* 在其余情况下，临界点 $$x_0$$ 不是局部极值。 -->

# Hermitian 矩阵

## 定义

Hermitian 矩阵是复数方阵，也称为共轭对称矩阵，即对矩阵每个第$$i$$ 行第 $$j$$ 列元素有：

$$a_{i, j} = \overline{a_{j, i}}$$

该矩阵也称为 Hermite 矩阵，厄米特矩阵或埃尔米特矩阵。

# Toeplitz 矩阵

## 定义

从左下到右上对角线为常数的矩阵为 Topelitz 矩阵，也称为 常对角矩阵。

即：

$$\mathbf{A} = \left[\begin{matrix}
a_0 & a_{-1} & a_{-2} & \cdots & \cdots & a_{-(n - 1)} \\
a_1 & a_0 & a_{-1} & \ddots & & \vdots \\
a_2 & a_1 & \ddots & \ddots & \ddots & \vdots \\
\vdots & \ddots & \ddots & \ddots & a_{-1} & a_{-2} \\
\vdots & & \ddots & a_1 & a_0 & a_{-1} \\
a_{m - 1} & \cdots & \cdots & a_2 & a_1 & a_0
\end{matrix}\right].$$

- 当 $$n = m$$ 且 $$a_i = a_{i + n}$$，则称该对角矩阵为循环矩阵；
- 当 $$n = m$$ 且 $$a_i = a_{-i}$$，则称该对角矩阵为 Hankel 矩阵。

# Cauchy 矩阵

## 定义

给定数域 $$\mathbb{F}$$，设 $$x_i, y_j\in\mathbb{F}$$，序列 $$(x_i), (y_j)$$ 内的元素互不相等。

如果对于 $$m\times n$$ 矩阵的元素 $$a_{i,j}$$ 有如下形式：

$$a_{i,j} = \frac{1}{x_i - y_j}$$

其中，$$x_i - y_j \neq 0, 1\leq i\leq m, 1\leq j\leq n$$

> 当 $$x_i - y_j = i + j - 1$$ 时，则该矩阵称为 Hilbert 矩阵。

# Gramian 矩阵

## 定义

一个列向量（矩阵）与其共轭对称的向量（矩阵）的内积，称为 Gramian 矩阵。

- Hibert 矩阵，也是特殊的 Gramian 矩阵。可以考虑 $$\mathbf{H}_{i, j} = \int_0^1 x^{i + j - 2}dx$$；
- 如果向量是中心随机变量[^1]，所得 Gram 矩阵也称为 协方差矩阵。

Gramian 矩阵，也称为 Gram 矩阵 或 格拉姆矩阵。


*[中心随机变量]: Centered Random Variable

[^1]: 如果该随机变量的平均值为 0，则称为中心随机变量

