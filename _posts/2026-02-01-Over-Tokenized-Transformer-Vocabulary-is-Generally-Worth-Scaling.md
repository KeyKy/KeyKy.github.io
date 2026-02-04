---
layout: post
title: Over-Tokenized Transformer Vocabulary is Generally Worth Scaling
---

## 个人思考

[论文](https://arxiv.org/pdf/2501.16975)发现对数线性放缩规律（log-linear scaling law）。通过指数级放大输入的词汇尺寸可以得到线性下降的训练损失。类似结构出现在[Deepseek Engram](https://www.arxiv.org/pdf/2601.07372)和[LongCatFlashLite](https://arxiv.org/pdf/2601.21204)。


## 论文方案

论文主要思路就是，给以前的大部分都是1-gram的vocabulary，增加2-gram，3-gram。由于n-gram是高度稀疏的因此通过hash实现新的Embedder。相关模型结构可以参考LongCatFlashLite的开源模型，论文有伪代码。
