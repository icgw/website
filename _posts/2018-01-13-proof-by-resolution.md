---
title: 命题逻辑归结演绎推理
teaser: 自动定理证明的主要方法
category: 理论篇
tags: [人工智能]
---

合取范式 (CNF) 的转换
------------
1. 消去 $$\Leftrightarrow$$，$$\alpha\Leftrightarrow\beta$$ 替换为 $$(\alpha\Rightarrow\beta)\wedge(\beta\Rightarrow\alpha)$$
2. 消去 $$\Rightarrow$$，$$\alpha\Rightarrow\beta$$ 替换为 $$\neg\alpha\vee\beta$$
3. 移动 $$\neg$$ 至内部，运用 De Morgan's 定律和 $$(\neg\neg)$$ 规则
4. 运用 $$\vee$$ 对 $$\wedge$$ 的分配律

上述过程，在多项式时间内完成。

基于合取范式的归结演绎规则
-----------------------
归结原理，又称为消解原理。


$$\begin{matrix} l_1\vee\dots\vee l_k,\ \ \  m_1\vee\dots\vee m_n \\ \hline l_1\vee\dots\vee l_{i-1}\vee l_{i+1} \vee\dots\vee l_k\vee m_1\vee\dots\vee m_{j - 1}\vee m_{j + 1}\vee\dots\vee m_n \end{matrix}$$

其中，$$l_i$$ 与 $$m_j$$ 是互为 _补文字_ 

简单的归结算法
------------
```python
    def PL_Resolution(KB, alpha):
        # 将 KB, alpha 转化为合取范式的子句集
        clause = CNF(KB, alpha)
        new    = set()
        while True:
            # 从子句集里抽取所有可能组合序对进行归结
            for C1, C2 in itertools.combinations(clause, 2):
                resolvents = PL_Resolve(C1, C2)
                # 归结出空子句，则返回 True
                if resolvents is None:
                    return True
                # 添加归结式
                new = new.append(resolvents)
            # 如果新产生的归结式集合是子句集合，则返回 False
            if new in clause:
                return False
            # 更新子句集
            clause = clause.union(new)
```

归结是可靠且完备的
---------------

1. 子句集 $$S$$ （由 $$KB\wedge\neg\alpha$$ 转化为合取范式的子句集）的归结子句，记为 $$RC(S)$$，定义为：由 $$S$$ 归结得到的所有子句组成的集合。
2. 算法 *PL_Resolution* 找到的最后子句集即 $$RC(S)$$
3. $$RC(S)$$ 是有限的，因此算法 *PL_Resolution* 总是终止的
4. $$KB\models\alpha \Leftrightarrow S $$ 是不可满足的

### 可靠性 ###

##### 如果 $$RC(S)$$ 包含空子句，那么 $$S$$ 是不可满足的。#####

* 将问题转换为证明下面结论即可。

如果 $$L, M\vdash R$$，那么 $$L, M\models R$$

其中，

$$L = l_1\vee\dots\vee l_k$$

$$M = m_1\vee\dots\vee m_n$$

$$R = l_1\vee\dots\vee l_{i-1}\vee l_{i+1} \vee\dots\vee l_k\vee m_1\vee\dots\vee m_{j - 1}\vee m_{j + 1}\vee\dots\vee m_n$$


$$l_i$$ 与 $$m_j$$ 是互为 _补文字_ 

> __证明__ ：反证法。假设 $$L, M\not\models R$$，则存在真假赋值 $$v$$ 使得，
> 
> $$L^v = True,\ M^v = True,\ R^v = False$$
> 
> 1. 由 $$R^v = False$$，有 $$l_p^v = False,\ m_q^v = False\ (1\leq p\neq i\leq k,\ 1\leq q\neq j\leq n)$$
> 2. 由于 $$l_i$$ 与 $$m_j$$ 是互为 _补文字_ ，故 $$L^v, M^v$$ 必有一个为 $$False$$，矛盾。
> 
> 综上，假设不成立。$$\Box$$

### 完备性：__Ground Resolution Theorem__ ###

##### 如果 $$S$$ 是不可满足的，那么 $$RC(S)$$ 包含空子句。 #####

> __证明__ ：往证其逆否命题，如果 $$RC(S)$$ 不含有空子句，则 $$S$$ 是可满足的。
> 
> 设 $$S$$ 中的原子命题为 $$P_1, \dots, P_k$$，因为 $$\emptyset\not\in RC(S)$$，构造 $$S$$ 的模型，如下。
> 
> $$i$$ 从 $$1$$ 到 $$k$$ 循环下述步骤：
> 
> - 如果 $$RC(S)$$ 中含有文字 $$\neg P_i$$ 的子句，并且该子句的其他文字在对 $$P_1, P_2, \dots, P_{i - 1}$$ 指派真假后都为 $$False$$ ，那么指派 $$P_i$$ 为 $$False$$
> - 否则，指派 $$P_i$$ 为 $$True$$
> 
> 按上述过程对 $$P_1, P_2, \dots, P_k$$ 的真假指派是 $$S$$ 的模型，即 $$S$$ 是可满足的。
> 
> 反证法。假设 $$S$$ 不满足，则存在 $$S$$ 的子句，其赋值为$$False$$，该子句必然有这样形式：$$False\vee\dots\vee P_i$$ 或 $$False\vee\dots\vee\neg P_i$$，然而，根据我们的构造方式，该子句为 $$True$$，矛盾。
> 
> 综上，假设不成立。$$\Box$$

### 确定子句和霍恩子句：提升推理效率 ###

* __确定子句__ 是指 _恰好_ 有一个肯定文字。
* __霍恩子句__ 是指 _至多_ 有一个肯定文字。

> 霍恩子句关于归结演绎是 __封闭的__ 。即两个霍恩子句归结后还是霍恩子句。

显然，所有确定子句都是霍恩子句。没有任何肯定文字的霍恩子句，叫做 __目标子句__ 。

简单而言，

<center> 霍恩子句 ::= 确定子句 | 目标子句 </center>

确定子句都可以写成形如：$$(p_1\wedge p_2\wedge\dots\wedge p_l)\Rightarrow p$$

目标子句都可以写成形如：$$(p_1\wedge p_2\wedge\dots\wedge p_l)\Rightarrow False$$

<mark> 采用霍恩子句进行推演，计算复杂度与知识库规模是线性关系！！！</mark>

##### 前向、后向推理 #####

```python
   def PL_FC_ENTAILS(KB, alpha):
       """
       : KB 是确定子句集
       : alpha 是要询问的命题
       """
       # 记录前件的符号个数的表格，例如：count[c] 表示子句 c 的前件符号个数
       count = TABLE_NUMBER_OF_SYMBOLS
       
       # 初始化所有符号指派为 False，例如：inferred[s] 表示符号 s 的真假值
       inferred = TABLE_INIT
       
       # 初始化 KB 中为 True 的作为符号队列
       agenda = QUEUE_SYMBOLS
       
       while agenda:
           p = agenda.pop()
           if p == q:
               return True
           if inferred[p] == False:
               inferred[p] = True
               for c in KB:
                   if p in c.Premise:
                       count[c] = count[c] - 1
                   if count[c] == 0:
                       agenda.append(c.Conclusion)
       return False
```

*[子句]: clause    
^
*[空子句]: empty clause
^
*[合取范式]: conjunctive normal form
^
*[文字]: literal
^
*[归结]: resolution
^
*[归结子句]: resolution clauses
^
*[霍恩子句]: horn clauses
^
*[确定子句]: definite clauses
^
*[目标子句]: goal clauses
^
*[归结策略]: a resolution algorithm
^
*[不可满足的]: 不存在模型（或赋值）使其所有子句为真。
^
*[肯定文字]: postive literal, 即不含否定符号的原子命题
