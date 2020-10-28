## 拉格朗日乘子 KKT条件

![image-20191216142046972](C:\Users\xzyun2011\AppData\Roaming\Typora\typora-user-images\image-20191216142046972.png)

深入理解拉格朗日乘子法（Lagrange Multiplier) 和KKT条件

https://www.cnblogs.com/mo-wang/p/4775548.html

![image-20191216142313865](C:\Users\xzyun2011\AppData\Roaming\Typora\typora-user-images\image-20191216142313865.png)

**Lagrange**拉格朗日函数 ，$\lambda, \nu$ lagrange 乘子，**L**是$f_{0}$ 的下界
$$
L(x, \lambda, \nu)=f_{0}(x)+\sum_{i=1}^{m} \lambda_{i} f_{i}(x)+\sum_{i=1}^{p} \nu_{i} h_{i}(x)
$$
**Lagrange**对偶函数 **$g(\lambda, \nu)$**
$$
\min _{x} f_{0}(x)=p^{*} \geq \inf _{x} L(x, \lambda, \nu)=g(\lambda, \nu)
$$
**Lagrange**对偶问题，即最优解$p^{*}$ 的最好下界：
$$
\begin{array}{ll}{\max .} & {g(\lambda, \nu)} \\ {\text {s.t.}} & {\lambda_{i} \geq 0, i=1, \cdots, m}\end{array}
$$
假设上述对偶问题最优解为$d^{*} $ ，是$p^{*}$的下界，有弱对偶性 $ d^{*} \leq p^{*}$； 但如果$d^{*}=p^{*}$成立则是强对偶性

	The strong duality does not hold in general
	The strong duality usually holds for convex problems

斯坦福大学 凸优化 对偶 https://zhuanlan.zhihu.com/p/54135029

