---
layout: default
title: Fourier Transform
description: 傅里叶变换
date: 2022-2-10 10:25:00 +0800
categories: [Signals and Systems]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Fourier Series

## Orthogonal Basis Functions

The 'orthogonal basis functions' are a set of functions of time, $$\phi(t)$$, such that the followings holds over some specified time interval $$T$$,

$$\forall k,\forall m,k \neq m, \int_{T} \overline{\phi_k(t)} \phi_m(t) =0$$

## Triangle Fourier Series

the 'OBF' of triangle fourier series are as follows

$$\{cos(nw_0t),sin(nw_0t)\}$$

which satisfy that

$$\int_Tcos(nw_0t)sin(mw_0t)dt = 0$$

$$\int_Tcos(nw_0t)cos(mw_0t)dt = \int_Tsin(nw_0t)sin(mw_0t)dt = \begin{cases} \frac{T}{2},m=n\\ 0,m\neq n \end{cases}$$

$$\int_T1dt=T$$

Therefore, we can express a periodic signal with fundamental period T as a sum of sinusoids,

$$x(t) = a_0 + \sum_{k=1}^{N} \{ a_kcos(kw_0t)+b_ksin(kw_0t) \} $$

where dc component $$a_0$$ , k-th harmonic $$a_k$$ and $$b_k$$ can be computed by

$$a_0=\frac{1}{T}\int_{0}^{T}f(t)dt$$

$$a_k=\frac{2}{T}\int_{0}^{T}f(t)cos(kw_0t)dt$$

$$b_k=\frac{2}{T}\int_{0}^{T}f(t)sin(kw_0t)dt$$

## Dirichlet Conditions

A periodic signal can be expressed by fourier series if and only if

* absolutely integrable, that is

$$\forall a,\int_a^{a+T}|x(t)|dt<\infty$$

* finite number of maxima and minima over any period
* finite number of discontinuities over any period