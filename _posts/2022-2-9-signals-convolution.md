---
layout: default
title: Signal's Convolution
description: 信号的卷积运算
date: 2022-2-9 10:35:00 +0800
categories: [Signals and Systems]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Moving Average(MA) filter

N-points MA filter is defined as

$$y[n]=\sum_{i=0}^{N-1}\frac{1}{N}x[n-i]$$

where N is a positive integer.

For example, in the 3-points MA filter, the output is 

$$y[n]=\frac{1}{3}x[n]+\frac{1}{3}x[n-1]+\frac{1}{3}x[n-2]$$

As a general class of system, the input/output relationship is defined as

$$y[n] = \sum_{i=0}^{n}w_ix[n-i],n\ge 0$$

it turns out that any 'causal linear time-invariant' DT system with the input x[n] equal to 0 for all n < 0 can be expressed as above.

Then, if $$x[n] = \delta[n]$$, we get the 'unit-pulse response' 

$$h[n] = \sum_{i=0}^{n}w_i\delta[n-i]=w_n,n\ge 0$$

# 2. Convolution

We use the symbol '*' to indicate convolution, that is

$$h[n]*x[n]=\sum_{i=0}^{n}h[i]x[n-i]$$

note that the convolution is defined for arbitrary DT signals that are not necessarily be 0 for all n < 0.

Given a system, it is determined completely by the unit-pulse response $$h[n]$$.

As for continuous-time signals, the convolution is defined

$$x(t)*v(t)=\int_{-\infty}^{+\infty}x(\lambda)v(t-\lambda)d\lambda$$

## Property

* commutative
* casual*casual -> casual

## Graphical Approach

* $$x(t) \rightarrow x(\lambda)$$
* $$v(t) \rightarrow v(\lambda) \stackrel{flip}{\longrightarrow} v(-\lambda) \stackrel{shift}{\longrightarrow} v(t-\lambda)$$
* $$\int_{-\infty}^{+\infty}x(\lambda)v(t-\lambda)d\lambda$$

# 3. Difference Equation & Differential Equation

In many cases, a casual linear time-invariant system is expressed by difference equation instead of convolution model.

in progress...