# 玻尔兹曼分布的变分法推导

## 问题本质：泛函极值问题

在推导玻尔兹曼分布的过程中，我们的目标是：

> 在所有可能的粒子数分布 $\{a_l\}$ 中，找出使系统微观状态总数（即 $\Omega$）最大的那个分布。

由于 $\Omega$ 通常极大，我们实际最大化的是其对数形式：

$$
\text{Maximize:} \quad \ln \Omega[\{a_l\}]
$$

这就是一个泛函的极值问题。


## 带约束的变分问题

我们在最大化 $\ln \Omega$ 的同时，需要满足两个物理约束条件：

$$
\begin{aligned}
\text{粒子数守恒：} \quad & \sum_l a_l = N \\
\text{能量守恒：} \quad & \sum_l a_l \epsilon_l = E
\end{aligned}
$$

这正是变分法中典型的带约束极值问题。

我们使用拉格朗日乘子法，引入乘子 $\alpha$ 和 $\beta$，构造函数：

$$
\mathcal{L}[\{a_l\}]
=
\ln \Omega[\{a_l\}]
-
\alpha \left( \sum_l a_l - N \right)
-
\beta \left( \sum_l a_l \epsilon_l - E \right)
$$

令变分

$$
\delta \mathcal{L} = 0
$$

对每一个 $a_l$ 施加变分，得到

$$
\frac{\partial \ln \Omega}{\partial a_l}
-
\alpha
-
\beta \epsilon_l
=
0
$$

这最终导出玻尔兹曼分布的形式：

$$
a_l \propto \omega_l e^{-\beta \epsilon_l}
$$
