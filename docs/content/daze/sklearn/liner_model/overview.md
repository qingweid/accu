# 广义线性模型

线性模型(Linear Model)是机器学习中应用最广泛的模型, 指通过样本特征的线性组合来进行预测的模型(即回归). 其中目标值是输入变量 x 的线性组合. 在数学概念中:

$$
f(x, w) = w_0 + w_1x_1 + ... + w_px_p = w^Tx + b
$$

其中 $x=[x_1, x_2, ..., x_p]$, $w=[w_1, w_2, ..., w_p]$, $b$ 为常数.

注: 在其他地方你可能会见到 $f(x, w) = w^Tx$ 的表示, 此时 $x=[1, x_1, x_2, ..., x_p]$, $w=[w_0, w_1, w_2, ..., w_p]$, 分别为 p+1 维的**增广特征向量**和**增广权重向量**.

在线性回归问题中, 可以直接用 $f(x, w)$ 来预测输出目标. 但在分类问题中, 由于输出目标是一些离散的标签或者是这些标签的后验概率而 $f(x, w)$ 的值域为实数, 因此无法直接用来进行预测, 需要引入一个非线性的**激活函数**(Activation Function) $g$ 来预测输出目标.

对于简单的两分类模型, 激活函数 $g$ 可以为阶跃函数:

$$
g(x, w) = 
\begin{cases}
    +1 & w^Tx+b > 0 \\\
    -1 & w^Tx+b < 0
\end{cases}
$$

上述公式定义了一个典型的两类分类问题的线性决策函数, 在高维的特征空间中, 所有满足 $w^Tx+b=0$ 的点组成一个分割超平面(Hyperplane). 这个超平面将特征空间一分为二, 划分成两个区域, 每个区域对应一个类别. 因此, 这个分割超平面也称为**决策边界**或**决策平面**. 在二维空间中, 决策边界为一个直线. 在三维空间中, 分类界面为一个平面. 在高维空间中, 分类界面为一个超平面. 对于线性分类器而言, 其权重向量与决策平面正交.

对于线性分类模型来说, 一个关键的问题是如何学习参数 $w$ 和 $b$, 也就是如何定义损失函数以及优化方法.
