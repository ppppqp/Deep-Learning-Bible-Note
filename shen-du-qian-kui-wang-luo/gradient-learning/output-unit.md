# Output Unit

代价函数的选择输出单元密切相关。

{% hint style="info" %}
输出单元指的是喂到代价函数中的输入，相当于最后一层隐藏层
{% endhint %}

### 1. 用于高斯分布的线性单元

{% hint style="info" %}
给定特征$$h$$，线性单元输出$$\hat y = W^{T}h + b$$。
{% endhint %}

线性单元输出层经常被用来产生**条件高斯分布的均值：**$$p(y|x)=\mathit{N}(y; \hat y, I)$$理解为如果向unit输入$$x$$，得到输出$$\hat y ​$$ ​​ 。那么认为$$p(y|x)$$符合均值为$$\hat y$$标准差为$$I$$的高斯分布\([来自这里](https://windmissing.github.io/Bible-DeepLearning/Chapter6/2Gradient/2OutputUnit/1Linear.html)\)。 我个人理解是线性单元只做平移和scale，在这个过程中**，平移会线性地变换均值，而scale不会改变均值**。所以可以应用在调整均值的任务上。



### 2. 用于Bernoulli输出分布的sigmoid单元

 对于预测二值型变量的问题，可以使用sigmoid单元。这时候，我们的输出**应当为一个0和1之间的数**（只需要一个，因为另一个用1减就行了）。我们考虑使用线性单元逼近：$$P(y=1|x) = max\{0, min\{1, w^{T}h+b\}\}$$

然而，这个在超过0和1的范围外，是平的，梯度是0，对优化很不利。所以，提出了sigmoid函数。

{% hint style="info" %}
$$\hat y = \sigma(w^{T}h+b)$$

理解成使用线性单元逼近，再转换成概率
{% endhint %}

如何通过sigmoid构造概率分布？sigmoid只能保证输出在0～1之间。如果输出两个数，则不一定和为1。

* 我们可以除以一个合适的常数来使他们和为1（归一化）
* 假设非归一化的对数概率对$$y$$和$$z$$是线性的，则可以取指数，再归一化。类似softmax



