## proximal 近端梯度

#### **1.1 次梯度 Subdifferential (or sub-gradient):**

Lasso优化：次梯度和近端梯度下降https://zhuanlan.zhihu.com/p/86824796

**Lipschitz用公式来描述如下：**
$$
\|\nabla f(x)-\nabla f(y)\| \leq L\|x-y\|, \quad x, y \in R^{n}
$$
Let $f \in \mathcal{P}$ be a convex (continuous) function. the subdifferential is denoted $\partial f$ and is defined by。例如$f(x)=|x|$在x=0处次梯度为【-1,1】
$$
\partial f(x)=  \lbrace \mathrm{v} \in \mathbb{R}^{n} \mid \forall \mathrm{y} \in \mathbb{R}^{n} \quad f(\mathrm{y}) \geq f(\mathrm{x})+\langle\mathrm{v}, \mathrm{y}-\mathrm{x}\rangle \rbrace
$$
![img](https://pic3.zhimg.com/80/v2-e4e4bf7852a297809a54224ae1228dba_hd.jpg)

$f(x)=\sum_{i=1}^{n} f_{i}\left(x_{i}\right)$ where $f_{i}$ are convex functions.，$\partial f(\mathrm{x})=\left(\partial f_{i}\left(x_{i}\right)\right)_{i=1}^{n}$

不可导最优条件Necessary and suﬃcient condition to deﬁne a minimizer in the convex, non diﬀerentiable case：
$$
\hat{\mathrm{x}}=\underset{\mathrm{x} \in \mathbb{R}^{n}}{\arg \min } f(\mathrm{x}) \Longleftrightarrow 0 \in \partial f(\hat{\mathrm{x}})
$$

* $(x \in \mathbb{R}), f(x)=\frac{1}{2}(x-d)^{2}+\lambda|x|$，$\underset{x \in R}{\arg \min } f(x)$ = Soft Threshold function. 软阈值

![image-20191216150551279](https://raw.githubusercontent.com/xzyun2011/study-notes/main/img/20201028215843.png)

* $ (x \in \mathbb{R}), f(x)=\frac{1}{2}(x-d)^{2}+\lambda|x|_{0} $ where $|x|_{0}=x$ if $x \neq 0$ and $|0|_{0}=0$，$ \underset{x \in R}{\arg \min } f(x) $ = Hard Thresholding function. 硬阈值

![image-20191216150751538](https://raw.githubusercontent.com/xzyun2011/study-notes/main/img/20201028215850.png)

#### **2.1 Moreau-Yosida regularization ** 莫罗-吉田正则化

**共轭函数(Conjugate Function)**

设函数$f: R^{n} \rightarrow R$，共轭函数为$f^{*}: R^{n} \rightarrow R$，定义域是使得下面公式sup结果小于 ![[公式]](https://www.zhihu.com/equation?tex=%5Cinfty)的部分
$$
f^{*}(y)=\sup _{x \in \operatorname{dom} f} y^{T} x-f(x)
$$
![img](https://pic1.zhimg.com/80/v2-a4e97ca16f2449cddf9cd6ae3aefb324_hd.jpg)

**莫罗包络** The Moreau envelope or Moreau-Yosida regularization ,$f_{\mu}(x)=\mathbb{R}^{n},$  $f_{\mu}(x)$ is convex.
$$
f_{\mu}(x)=\inf _{y}  \lbrace f(y)+\frac{1}{2 \mu}\|x-y\|_{2}^{2} \rbrace
$$
莫罗包络本质上是函数*f*的一个平滑或者正则化的形式，1、其定义域为$R^{n}$（即使函数*f*的定义域不是$R^{n}$*）2、连续可微。（即使当函数*f*不连续可微时）3、函数* $f$和$f_{\mu}(x)$最小值集合是相同的。

**莫罗分解，Moreau's Decomposition**

An important identity is Moreau's decomposition, which states that
$$

\operatorname{prox}_{f}(x)+\operatorname{prox}_{f^{*}}(x)=x
$$
**例子$f(x)=|x|$，**
$$
f_{\mu}(x)=\inf _{y} \lbrace |y|+\frac{1}{2 \mu}(x-y)^{2}\rbrace=\left\{\begin{array}{ll}{\frac{1}{2 \mu} x^{2},} & {|x| \leq \mu} \\ {|x|-\frac{\mu}{2},} & {|x|>\mu}\end{array}\right.
$$
![image-20191216164351063](https://raw.githubusercontent.com/xzyun2011/study-notes/main/img/20201028215944.png)

**近端操作可以看做是最小化函数$f_{\mu}(x)$的一个梯度步骤，步长为*λ***
$$
\operatorname{prox}_{\lambda f}(x)=x-\lambda \nabla f_{\mu}(x)
$$

#### **2.2 Proximal operator**

Let f be a function in P, convex and lsc.
$$
\operatorname{prox}_{f}(\mathrm{x}):=\underset{\mathrm{y} \in \mathbb{R}^{n}}{\arg \min }\lbrace\frac{1}{2}\|\mathrm{y}-\mathrm{x}\|^{2}+f(\mathrm{y})\rbrace
$$
The minimum is reached in yˆ(x) = yˆ such that 
$$
\begin{array}{l}{0 \in \partial f(\hat{y})+\hat{y}-x} \\ {x \in \hat{y}+\partial f(\hat{y})} \\ {\hat{y} \in(I+\partial f)^{-1}(x)}\end{array}
$$

**近端操作$\operatorname{prox}_{f}$*和次微分$\partial f(x)$之间的关系 $\operatorname{prox}_{\lambda f}=$$$
(I+\lambda \partial f)^{-1}
$$**
$$
\text { The elements of prox } f(x) \text { are the elements of }(I+\partial f)^{-1}(x)
$$

**不可导凸函数最优条件，Let $f \in \mathcal{P}$ be a convex, lsc subdifferentiable function.**:
$$
\hat{\mathrm{x}}=\underset{\mathrm{x} \in \mathbb{R}^{n}}{\arg \min } f(\mathrm{x}) \Longleftrightarrow \hat{\mathrm{x}}=\operatorname{prox}_{f}(\hat{\mathrm{x}})
$$
**性质**（https://zhuanlan.zhihu.com/p/37190315）：

* $f\left(x_{1}, \ldots, x_{m}\right)=\sum f_{i}\left(x_{i}\right),则 \operatorname{prox}_{f}\left(x_{1}, \ldots, x_{m}\right)=\operatorname{prox}_{f_{1}}\left(x_{1}\right) \times \ldots \times \operatorname{prox}_{f_{m}}\left(x_{m}\right)$