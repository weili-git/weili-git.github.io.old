---
layout: default
title: Signal's Properties
description: 信号的性质
date: 2022-2-8 19:58:00 +0800
categories: [Signals and Systems]
permalink: /:title    # permalink: /:categories/:title
---

# 1.Periodic Continuous-Time Signals

given two periodic CT signals

$$\forall t, x_1(t+T_1) = x_1(t)$$

and

$$\forall t, x_2(t+T_2) = x_2(t)$$

if the sum of them is periodic, then

$$\forall t, x_1(t+T)+x_2(t+T)=x_1(t)+x_2(t)$$

it is satisfied if and only if

$$\exists p,q \in N^*, T=pT_1=qT_2$$

in other word, p and q are coprime

$$\frac{T_1}{T_2}=\frac{p}{q}\in Q$$

# 2. Sifting Property

note that $$\forall \lambda \neq t_1, \delta(\lambda-t_1)=0$$

it follows that

$$\int_{-\infty}^{+\infty}f(\lambda)\delta(\lambda-t_1)d\lambda=\int_{t_1-\epsilon}^{t_1+\epsilon}f(\lambda)\delta(\lambda-t_1)d\lambda=f(t_1)$$

where $$f(t)$$ is continuous at $$t=t_1$$

# 3. Periodic Discrete-Time Signals

periodic DT signal satisfies that

$$\forall t\in N^*, x_1[n+r] = x_1[n]$$

if it is sinusoid signal, then

$$Acos[\Omega n+\theta]=Acos[\Omega n+\Omega r + \theta]=Acos[\Omega n+2\pi q + \theta]$$

which means that

$$\Omega = \frac{2\pi q}{r},q,r\in N^*$$

# 4. Property

* Linearity
* Time Invariance
* Casuality
* Memory

