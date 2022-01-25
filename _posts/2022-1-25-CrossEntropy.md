---
layout: default
title: Cross Entropy
description: 交叉熵损失函数
date: 2022-1-25 11:58:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Review of Entropy

Entropy is usually used to represent the average amount of self-information. The calculation formula is as follows:

$$H(X) = E(log\frac{1}{p_i}) = -\sum_{i=1}^{n}p_ilogp_i $$

For example, supposed that we have a probability distribution X = [0.7, 0.3]. Then we have,

$$H(X) = -0.7log0.7-0.3log0.3 = 0.88 bit$$

What's more, we can easily find that
$$0\le H(X) \le logn$$
is always true.

The proof of the left inequality is trivial because
$$0\le p\le 1$$
the equality is established if and only if
$$p_i=1$$

As for the right hand side, we take n=3 as the example

$$H(X) = -p_1logp_1-p_2logp_2-(1-p_1-p_2)log(1-p_1-p_2)$$

Let the partial derivatives be zero,

$$\frac{\partial H(X)}{\partial p_1} = log(\frac{1-p_1-p_2}{p_1})=0$$

then we have,

$$p_1=p_2=1-p_1-p_2=\frac{1}{3}$$

and finally we get the maximum,

$$H(X)_{max} = log3$$

# 2. KL Divergence & Cross Entropy

KL divergence is used to indicate the distance of two different distribution.

$$D(p||q) = \sum_{i=1}^{n}p_ilog(\frac{p_i}{q_i})$$

From the formula, we know that usually
$$D(p||q) \ne D(q||p)$$
Conventionally, we set p as the real distribution and q as the predicted distribution.

As an example, set p = [1, 0, 0] and q = [0.7, 0.2, 0.1] then 

$$D(p||q) = 1*log(\frac{1}{0.7}) = 0.51bit$$

The relationship of KL divergence, Cross Entropy and Entropy is:
$$D(p||q) = H(p,q) - H(p)$$

Therefore, the formula of Cross Entropy is 

$$H(p, q) = -\sum_{i=1}^{n}p_ilogq_i$$

It is used to represent the difference of two distribution.

# 3. Softmax & Logistic Regression

set

$$X = [x_1, x_2, ..., x_n]$$

then

$$Y = [\frac{e^{x_1}}{\sum_{i=1}^{n}e^{x_i}}, \frac{e^{x_2}}{\sum_{i=1}^{n}e^{x_i}}, ..., \frac{e^{x_n }}{\sum_{i=1}^{n}e^{x_i}}] = [y_1, y_2, ..., y_n] = \frac{exp(X)}{\bold1^Texp(X)}$$

if we use the Cross Entropy Loss, then

$$loss = -\hat Y^Tlog(Y) = -\hat Y^Tlog(Wx-\bold1log(\bold1^Texp(Wx))) = -\hat Y^TWx+log(1^Texp(Wx))$$

where
$$\hat Y^T\bold1 = 1$$
and since

$$d\sigma(X)=\sigma^{'}(X)\odot dX$$
$$tr(A^T(B\odot C)) = tr((A\odot B)^TC)$$

we have

$$dloss = -\hat Y^TdWx + \frac{\bold1^T(exp(Wx)\odot(dWx))}{\bold1^Texp(Wx)} = -\hat Y^TdWx + \frac{exp(Wx)^TdWx}{\bold1^Texp(Wx)}$$

$$= tr(-\hat Y^TdWx+softmax(Wx)^TdWx)=tr(x(softmax(Wx)-\hat Y)^TdW)$$

thus

$$\frac{\partial loss}{\partial W} = (softmax(Wx)-\hat Y)x^T$$
or
$$a=Wx,\frac{\partial loss}{\partial a} = softmax(a)-\hat Y$$

on the other hand, 

$$D_jS_i=\frac{\partial y_i}{\partial x_j} = \begin{cases}S_i(1-S_j) & i=j\\ -S_iS_j & i\ne j\end{cases}$$