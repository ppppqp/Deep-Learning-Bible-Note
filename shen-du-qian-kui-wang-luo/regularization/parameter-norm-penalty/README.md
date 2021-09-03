# Parameter Norm Penalty

通过对目标函数$$J$$添加一个参数范数惩罚$$\Omega(\theta)$$来限制模型的学习能力。

$$\widetilde J (\theta; X,y) = J(\theta; X,y)+\alpha\Omega(\theta)$$

我们会讨论不同范数$$\Omega$$对模型的影响。通常我们只惩罚权重（weight）而不惩罚偏置（bias），因为偏置更容易精确拟合。

