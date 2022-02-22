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

# 2. Example

Rectangular pulse train, T = 2.

$$x(t)=\frac{1}{2}+\frac{2}{\pi}\sum_{k=1}^{\infty}\frac{1}{k}sin(\frac{k\pi}{2})cos(k\pi t), -\infty<t<+\infty$$

which contains only odd harmonics.

In general, $$b_k=0$$ for even signals and $$a_k=0$$ for odd signals.

# Gibbs Phenomenon

9%, Omitted.

# 3. Complex Exponential Series

the expression of Complext Exponential Series of a periodic signal is

$$x(t)=\sum_{k=-\infty}^{+\infty}c_ke^{jkw_0t}, -\infty<t<+\infty$$

using Euler's formula, we can easily find that

$$c_0=a_0, c_k=\frac{1}{2}(a_k-jb_k), c_{-k}=\frac{1}{2}(a_k+jb_k), k=1,2,...$$

and we can also compute the coefficient by

$$c_k=\frac{1}{T}\int_{0}^{T}x(t)e^{-jkw_0t}dt,k=0,\pm 1, \pm 2,...$$

On the other hand,

$$a_0=c_0,a_k=c_k+c_{-k}=2Re(c_k),b_k=j(c_k-c_{-k})=-2Im{c_k}$$

# 4. Line Spectra

$$x(t)=a_0+\sum_{k=1}^{\infty}A_kcos(kw_0t+\theta_k)$$

amplitude spectra

$$|c_k|=|c_{-k}|=\frac{1}{2}\sqrt{a_k^2+b_k^2}=\frac{1}{2}A_k$$

phase spectra

$$\angle c_k=-\angle c_{-k}=tan^{-1}(-\frac{b_k}{a_k})=\theta_k$$

# 5. Parseval's Theorem

Average power of a signal is defined as

$$P=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x^2(t)dt$$

by parseval's theorem, it is equal to 

$$P=\sum_{k=-\infty}^{+\infty}|c_k|^2$$

proof is ommited.

## From 7.11

$$\int_{-\infty}^{+\infty}x^2(t)dt=\frac{1}{2\pi}\int_{-\infty}^{+\infty}\overline{X(\omega)}X(\omega)d\omega$$

# 6. Fourier Transform

Represent the aperiodic signal in terms of frequency contents, that is FT, and we'll show that it is defined for all real values (not line spectra)

$$X(\omega)=\int_{-\infty}^{+\infty}x(t)e^{-j\omega t}dt$$

which requires the condition

$$\int_{-\infty}^{+\infty}|x(t)|dt<\infty$$

## Exonential

$$e^{-at} \leftrightarrow \frac{1}{a+j\omega}$$

分子分母同时取模

$$|X(\omega)|=\frac{1}{\sqrt{a^2+\omega^2}}$$

分子相位-分母相位

$$\angle X(\omega)=-tan^{-1}\frac{\omega}{a}$$

## Rectangular Pulse

$$p_\tau(t) \leftrightarrow \tau Sa(\frac{\omega\tau}{2})$$

## Constant

$$1\leftrightarrow 2\pi \delta(\omega)$$

# 7. Property

## 7.1 real-imaginary

$$X(\omega)=\int_{-\infty}^{+\infty}x(t)cos\omega tdt - j\int_{-\infty}^{+\infty}x(t)sin\omega tdt=R(\omega)+jI(\omega)$$

$$|X(\omega)|=\sqrt{R^2(\omega)+I^2(\omega)}=|X(-\omega)|$$

$$\angle X(\omega) = tan^{-1}\frac{I(\omega)}{R(\omega)}=-\angle X(-\omega)$$

## 7.2 Linearity

omitted

## 7.3 Time Scaling

$$x(at) \leftrightarrow \frac{1}{|a|}X(\frac{\omega}{a})$$

## 7.4 Time Reversal

$$x(-t) \leftrightarrow X(-\omega) \leftrightarrow \overline{X(\omega)}$$

## 7.5 Multiplication by a Power of t

$$t^nx(t) \leftrightarrow (j)^n\frac{d^n}{d\omega^n}X(\omega)$$

## 7.6 Multiplication by a Complex Exponential

$$x(t)e^{j\omega_0t} \leftrightarrow X(\omega-\omega_0)$$

## 7.7 Multiplication by a sinusoid

ommited

## 7.8 Differentiation in the Time Domain

$$\frac{d^n}{dt^n}x(t) \leftrightarrow (j\omega)^nX(\omega)$$

## 7.9 Integration in the Time Domain

$$\int_{-\infty}^{t}x(\lambda)d\lambda \leftrightarrow \frac{1}{j\omega}X(\omega)+\pi X(0)\delta(\omega)$$

if there is no dc component,

$$\int_{-\infty}^{t}x(\lambda)d\lambda \leftrightarrow \frac{1}{j\omega}X(\omega)$$

## 7.10 Convolution in the Time Domain

$$x(t)*v(t) \leftrightarrow X(\omega)V(\omega)$$

## 7.11 Multiplication in the Time Domain

$$x(t)v(t) \leftrightarrow \frac{1}{2\pi}X(\omega)*V(\omega)$$

## 7.12 Duality

$$X(t) \leftrightarrow 2\pi x(-\omega)$$

page 142

# 8. Inverse Transform

$$x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty}F(\omega)e^{j\omega t}dt$$
