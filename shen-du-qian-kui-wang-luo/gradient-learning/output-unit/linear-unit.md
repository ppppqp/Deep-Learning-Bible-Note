# Linear Unit

### 用于高斯分布的线性单元

{% hint style="info" %}
给定特征$$h$$，线性单元输出$$\hat y = W^{T}h + b$$。
{% endhint %}

线性单元输出层经常被用来产生**条件高斯分布的均值：**$$p(y|x)=\mathit{N}(y; \hat y, I)$$理解为如果向unit输入$$x$$，得到输出$$\hat y ​$$ ​​ 。那么认为$$p(y|x)$$符合均值为$$\hat y$$标准差为$$I$$的高斯分布\([来自这里](https://windmissing.github.io/Bible-DeepLearning/Chapter6/2Gradient/2OutputUnit/1Linear.html)\)。 我个人理解是线性单元只做平移和scale，在这个过程中**，平移会线性地变换均值，而scale不会改变均值**。所以可以应用在调整均值的任务上。

