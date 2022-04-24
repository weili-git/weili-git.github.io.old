---
layout: default
title: Transposed Convolution
description: 转置卷积
date: 2022-4-7 18:16:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Function

ConvTransposed can be used to enlarge the width and height from the input.

# 2. Principle pad=0, strd=1

Fill the input into size kernel-1, then apply Transposed kernel Conv (主副对角线转置). 

# 3. General Case

Insert stride lines between rows/cols , then fill the input into size kernel-padding-1, then Transposed kernel Conv (k, 1, 0)

ConvTranspose2d


$$n^* = (n-1)s + k - 2p$$

Conv2d

$$n^* = floor( \frac{n -k + 2p + s}{s} )$$