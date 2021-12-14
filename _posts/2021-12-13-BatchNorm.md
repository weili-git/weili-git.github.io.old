---
layout: default
title: BatchNorm
description: Introduction to BatchNorm
date: 2021-12-13 10:05:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Preface
As the Neural Network grows deeper, there are a few questions.
- the loss comes at the end
    - the top layers train faster
    - the bottom layers train slowly
- the data is at the bottom
    - as the bottom layers update, all other layers need to change
    - the top layers retrain many times
    - slower convergence

# 2. BatchNorm

Fix mini-batch's mean and variance:

$$\mu_B=\frac{1}{|B|}\sum_{i\in B}x_i$$

and

$$\sigma_{B}^{2}=\frac{1}{|B|}\sum_{i\in B}(x_i-\mu_B)^2+\epsilon$$

additional adjustments (trainable parameters):

$$x_{i+1}=\gamma\frac{x_i-\mu_B}{\sigma_B}+\beta$$

- after 'Conv, Dense' before 'activation function'
- before 'Conv, Dense'
- 对于全连接层，作用于特征维
- 对于卷积层，作用于通道维

# 3. How it works

- Each batch has different 'mean' and 'variance', so we add noise to the batch and control the complexity of the model.
- It's not necessary to use it with Dropout
- learn proper offset and zoom to fix the mean and variance of the mini-batch data.
- speed up training, but doesn't increase accuracy. (greater lr is available)

# 4. Q&A
- shallow layer using BN may not have good results.
- Linear Layer is not likely to learn BN, which can stablize the data..