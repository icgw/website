---
title: 通过搜索来得到问题的解
teaser: 解决问题的一种方式
category: 技术类
tags: [计算机科学]
---

基于目标的智能体

问题求解智能体 (Problem-solving agents)
------------




搜索解空间
---------

* 状态空间 (States)
* 初始状态 (Initial state)
* 后继函数 (Transition Model)
	- 行动 (Actions)
	- 路径成本 (Path cost)
* 目标测试 (Goal test)

无信息搜索 (Uniformed Search Strategies)
---------

### 宽度优先搜索 ###



启发式搜索 (Informed(Heuristic) Search Strategies)
---------

### 贪婪搜索 ###

### A* 搜索：使搜索解的成本最小化 ###

__A* 搜索__ 亦称为 __最小成本优先搜索__ 。

设当前搜索的节点为第 $$n$$ 个节点。则

1. 从初始节点到当前节点的路径成本，记为 $$g(n)$$。
2. 从当前节点到目标节点的最小成本估计，记为 $$h(n)$$。

它包含两个函数，达到节点的成本函数 $$g(n)$$，从该节点获得目标值的成本 $$h(n)$$。

$$h(n)$$ 称为启发函数 (heuristic function)。

局部搜索
-------