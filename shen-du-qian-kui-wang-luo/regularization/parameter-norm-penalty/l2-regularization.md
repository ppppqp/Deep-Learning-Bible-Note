# L2 Regularization

### 太长不看版：

本文通过对比没有weight decay所得到的最优参数$$w^{*}$$和增加weight decay所得到的最优参数$$\widetilde w$$的关系，即$$\widetilde w = Q(D+\alpha I)^{-1}(DQ^{T})w^{*}$$ 得出了**weight decay可以保持**$$w$$**中能显著减小目标函数的参数，而衰减无助的参数的结论**。

### 正文

最简单常见的参数范数惩罚，通常被称为权重衰减（weight decay）的L2参数范数惩罚。这个策略通过向目标函数添加正则项$$\Omega(\theta)=\dfrac{1}{2}||w||^2_2$$使得权重更接近原点。

$$\widetilde J(w; X,y) = \dfrac{\alpha}{2}w^Tw + J(w; X,y)$$

梯度为$$\nabla{w}\widetilde J(w; X,y) = \alpha w + \nabla_w J(w;X,y)$$

更新权重的公式为：$$w \leftarrow (1-\epsilon \alpha)w - \epsilon\nabla_w J(w;X,y)$$

可见，权重衰减更改了学习规则。我们进一步比较差异。假设 $$w^*$$为没有使用权重衰减的最优权重向量，即$$w^* = \arg \min_w J(w)$$ 。我们在$$w^*$$的邻域对$$J$$做二次近似，即泰勒展开，保留到二阶项，有$$\hat J(\theta) = J(w^*) + \dfrac{1}{2}(w-w^*)^TH(w-w^*)$$，因为$$w^*$$是不使用weight decay时的最优解，**所以在该处一阶导数为零，即梯度为零，Hessian为半正定**。我们然后考虑使得$$\hat J(\theta)$$最小化，可以通过$$\nabla_w\hat J(w) = H(w-w^{*})=0$$得到。

> 泰勒展开公式：$$f(x) = f(x_0) + \dfrac{f^{\prime}(x_0)}{1!}(x-x_0) + \dfrac{f^{\prime\prime}(x_0)}{2!}(x-x_0)^2 + ...$$，对应到这里就是$$J(\theta) = J(w^*) + (w-w^*)^T\nabla_w J(w; X,y) +\dfrac{1}{2}(w-w^*)^T H(w-w^*)$$,但是非常好奇，**平方去哪里了？**

添加权重衰减的梯度，则有$$\alpha \widetilde w + H(\widetilde w - w^{*})=0$$，解出方程可得到$$\widetilde w =  (H + \alpha I)^{-1}H w^{*}$$ 。由于$$H$$是实对称的（Hessian矩阵），可以将它分解为对焦矩阵$$D$$和一组特征向量的标准正交基$$H=QDQ^{T}$$，代入得到$$\widetilde w =( QDQ^{T}+\alpha I)^{-1}(QDQ^{T})w^{*} = ( Q(D+\alpha I)Q^{T})^{-1}(QDQ^{T})w^{*} = Q(D+\alpha I)^{-1}(DQ^{T})w^{*}$$效果是沿着$$H$$的特征向量定义的轴缩放$$w^*$$的分量。**具体是以**$$\dfrac{\lambda_i}{\lambda_i+\alpha}$$**为因子缩放与**$$H$$**的第i个特征向量对齐的**$$w^{*}$$**的分量。**若沿着$$H$$特征值较大方向，即$$\lambda_i\gg a$$，受影响较小，反之亦然。只有在显著减少目标函数方向的参数会保留的比较完好，无助的参数会衰减掉。



总结来说，L2正则化能让学习算法感知到具有高方差的输入，因此对应特征的权重会收缩。

