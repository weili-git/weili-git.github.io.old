---
layout: default
title: Sequential Model
description: 序列模型
date: 2022-4-3 20:26:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Sequential Model

## 1.1 Conditional Probability

$$P(\bold x)=P(x_1)P(x_2|x_1)P(x_3|x_1,x_2)...P(x_t|x_1,x_2,...,x_{t-1})$$

## 1.2 Autoregressive Model

For ever-known model, we call it AR Model.

$$p(x_t|x_1,x_2,...,x_{t-1})=p(x_t|f(x_1,x_2,...,x_{t-1}))$$

## 1.3 Markov Model

By Markov Hypothesis, the current state is determined by previous$$\tau$$ points.

$$p(x_t|x_1,x_2,...,x_{t-1})=p(x_t|x_{t-\tau},...,x_{t-1})=p(x_t|f(x_{t-\tau},...,x_{t-1}))$$

## 1.4 Latent Model 潜变量模型

we use a variable to represent the inner states (RNN is one of the Latent Model)

$$h_t=f(x_1,...,x_{t-1})$$

$$x_t=p(x_t|h_t)$$

QA...