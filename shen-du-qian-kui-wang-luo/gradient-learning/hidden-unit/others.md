# Others

## 其他常见的隐藏单元包括：

1. 纯线性
2. softmax
3. Redial Basis Function RBF:
4. softplus
5. hard tanh

| Function Name | Equation | Feature |
| :--- | :--- | :--- |
| 纯线性 |  | 线性变化约束为低秩，可以减少参数 |
| softmax |  | k个可能的离散性随机变量的概率分布 |
| Radial Basis Function  | $$h_{i}=\exp(-\dfrac{1}{\sigma_{i}^{2}}||W_{:,i}-x||^2)$$ | 在$$x$$接近模版$$W$$时会很活跃，但对大部分$$x$$都饱和为0，很难优化 |
| softplus | $$\zeta(a) = \log(1+\exp(a))$$ | ReLU的平滑版本 |
| hard tanh | $$g(a) = \max(-1, \min(1,\tanh(a)))$$ | 有界 |

