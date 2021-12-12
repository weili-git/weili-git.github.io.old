---
layout: default
title: GoogLeNet
description: Introduction to GoogleNet
date: 2021-12-12 20:08:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Inception Block (v1)
Extract information from 4 different paths, and then concatenate them in output channel. It has less parameters and time complexity. The assignment of channels are based on the significance.

* 1x1 Conv  (64)
* 1x1 Conv  (96); 3x3 Conv, pad 1 (128)
* 1x1 Conv  (16); 5x5 Conv, pad 2 (32)
* 3x3 MaxPool, pad 1; 1x1 Conv  (32)

# 2. Architecture

![GoogLeNet](/assets/images/2021-12-12-1.png)

You can see that there are so many hyper-parameters (num of channels). So it has limited use.

# 3. Q&A
3x3 => 1x3, 3x1 less computation
channels 'power 2' make the best of gpu.