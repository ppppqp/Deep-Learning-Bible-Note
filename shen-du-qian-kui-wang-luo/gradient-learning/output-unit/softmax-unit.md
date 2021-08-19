# Softmax Unit

### 用于multinoulli输出分布的softmax单元

多个类别（多于两类）时，拓展logistic sigmoid。独特之处在于，softmax不仅可以作为输出单元，也可以在内部使用。

{% hint style="info" %}
softmax函数：一个argmax的可微版本

$$softmax (z)_{i} = \dfrac{\exp(z_{i})}{\sum _{j}\exp(z_{i})}$$
{% endhint %}

于是我们的loss function就变成了$$\log softmax(z)_{i} = z_{i} - \log\sum_{j}\exp(z_{j})$$, 可以近似为$$z_{i}-max_{j}z_{j}$$也就是说，如果$$i\neq j$$这个样本的loss将是一个很大的负数，如果$$i=j$$,这个样本的loss将接近0。

