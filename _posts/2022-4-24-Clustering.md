---
layout: default
title: Clustering
description: 聚类
date: 2022-4-24 17:16:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Definition

Formally, suppose that we have a dataset $$D=\{x_1,x_2,...,x_m\}$$, in which every sample is a n-dim vector. Clustering is to divide these data into k disjoint 'cluster' $$\{C_l \vert l=1,2,...,k\}$$. This is just like 'Disjoint Set' that we learn in algorithm course.

# 2. K-means

The intuition of K-means algorithm is very straight-forward. Initially, we choose k random samples $$\{ \mu_1,\mu_2,...,\mu_k \}$$ as the 'mean vector', which represent the center position of k cluster. Then, we scan through each sample in $$D$$ and mark them by the closest mean vector. After that, we update the 'mean vector' by the mean value of each cluster. After some iterations (or until the 'mean vector' doesn't change any more), we finally get the real 'mean vector' of each cluster.

For example, suppose that we have a dataset $$D=\{x_1,x_2,...,x_7\}$$, and we initially select $$\{ \mu_1, \mu_2, \mu_3 \} = \{ x_1, x_4, x_6\}$$, and then we obtain a division,

$$C_1 = \{x_1, x_2, x_5\}$$

$$C_2 = \{x_4, x_7\}$$

$$C_3 = \{x_3, x_6\}$$

Then, we calculate the new 'mean vector'.

$$\mu_1^*=\frac{1}{3}(x_1+x_2+x_5)$$

$$\mu_2^*=\frac{1}{2}(x_4+x_7)$$

$$\mu_3^*=\frac{1}{2}(x_3+x_6)$$

Repeat the process above, we'll have a good 'mean vector', which can denote the center position of each cluster.

# Outliers, Initial centroids

# KNN

Time complexity is related to the size of data.