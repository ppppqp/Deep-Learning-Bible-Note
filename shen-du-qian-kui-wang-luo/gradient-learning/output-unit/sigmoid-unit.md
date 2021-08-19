# Sigmoid Unit

### 用于Bernoulli输出分布的sigmoid单元

 对于预测二值型变量的问题，可以使用sigmoid单元。这时候，我们的输出**应当为一个0和1之间的数**（只需要一个，因为另一个用1减就行了）。我们考虑使用线性单元逼近：$$P(y=1|x) = max\{0, min\{1, w^{T}h+b\}\}$$

然而，这个在超过0和1的范围外，是平的，梯度是0，对优化很不利。所以，提出了sigmoid函数。

{% hint style="info" %}
$$\hat y = \sigma(w^{T}h+b)$$

理解成使用线性单元逼近，再转换成概率

其中，$$\sigma(x)=\dfrac{1}{1+e^{-x}}$$
{% endhint %}

如何通过sigmoid构造概率分布？sigmoid只能保证输出在0～1之间。如果输出两个数，则不一定和为1。

* 我们可以除以一个合适的常数来使他们和为1（归一化）
* 假设非归一化的对数概率对$$y$$和$$z$$是线性的，则可以取指数，再归一化。类似softmax

总的流程就是：

![](../../../.gitbook/assets/jie-ping-20210819-xia-wu-7.11.24%20%281%29.png)

使用公式说明:

$$\log \hat P = yz \\ \hat P(y) = \exp(yz)\\ P(y)=\dfrac{exp(yz)}{\sum^{1}_{ y^{\prime} =0}\exp (y^{\prime} z)} \\ P(y) = \sigma((2y-1)z)$$

则损失函数是：

$$J(\theta) = -\log P(y|x) = -\log \sigma((2y-1)z) = \zeta((1-2y)z)$$

{% hint style="info" %}
$$\zeta$$叫做softplus函数，$$\zeta(x) = \log (1+\exp(x)) = \log( \dfrac{\exp(-x)+1}{\exp(-x)}) = -\log\sigma(-x)$$
{% endhint %}

我们可以进一步看他何时会饱和：因为我们知道$$\zeta$$是在$$x<0$$的时候达到饱和，也就是说$$(1-2y)z < 0$$, $$z>0, y=1$$或者$$z<0, y=0$$，也就是说在判断正确的时候饱和。



