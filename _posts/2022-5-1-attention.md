---
layout: default
title: Attention
description: 注意力机制
date: 2022-5-1 20:43:00 +0800
categories: [Deep-learning]
permalink: /:title    # permalink: /:categories/:title
---

# 1. Input

There're 3 inputs Q(query), K(key), V(value) for attention mechanism. If Q=K=V, we call it 'self-attention'. Also, there're several rules to calculate it.

$$Attention(Q,K,V) = Softmax(Linear([Q,K])) \cdot V$$

$$Attention(Q,K,V) = Softmax(sum(\tanh(Linear([Q,K])))) \cdot V$$

$$Attention(Q,K,V) = Softmax(\frac{Q \cdot K^T}{\sqrt{d_k}}) \cdot V$$

The 'bmm' is a special tensor multiply operation, batch matrices multiplication.

$$(b, n, m)*(b, m, p) \rightarrow (b, n, p)$$

Attention is usually used in seq2seq task.

```python
import torch
import torch.nn as nn
import torch.nn.functional as F

class Attn(nn.Module):
    def __init__(self, query_size, key_size, value_size1, value_size2, output_size):
        # query_size, key_size代表最后一个维度
        # V尺寸为[1, value_size1, value_size2]
        super(Attn, self).__init__()
        self.query_size = query_size
        self.key_size = key_size
        self.value_size1 = value_size1
        self.value_size2 = value_size2
        self.output_size = output_size

        self.attn = nn.Linear(self.query_size + self.key_size, self.value_size1)

        self.attn_combine = nn.Linear(self.query_size + self.value_size2, self.outpu_size)

    def forward(self, Q, K, V):
        attn_weights = F.softmax( self.attn(torch.cat((Q[0], k[0]), 1)) , dim=1)
        attn_applied = torch.bmm(attn_weights.unsqueeze(0), V)
        output = torch.cat((Q[0], attn_applied[0]), 1)  # 降维
        output = self.attn_combine(output).unsqueeze(0)
        return output, attn_weights

query_size = 32
key_size = 32
value_size1 = 32
value_size2 = 64
output_size = 64

attn = Attn(query_size, key_size, value_size1, value_size2, output_size)
Q = torch.randn(1, 1, 32)
K = torch.randn(1, 1, 32)
V = torch.randn(1, 1, 64)
output = attn(Q, K, V)
print(output[0])
print(output[1])
```