---
layout: post
title: Megatron LM 心得
---

## 关于 1F1B 流水线并行调度图的讨论

在深入研究 Megatron-LM 源码后，我对官方文档的图示有了新的理解：

> "感觉 [NVIDIA 官方博客](https://developer.nvidia.com/blog/scaling-language-model-training-to-a-trillion-parameters-using-megatron/) 对 1F1B 气泡图（图 1）有误，目前结合 `forward_backward_pipelining_without_interleaving` 的源码实现来看，认为图 2 才是正确的。"

### 1F1B 调度对比

| 博客原图（图 1） | 源码推导修正图（图 2） |
| :---: | :---: |
| ![图 1](../images/pp_nvidia.png) | ![图 2](../images/pp2.png) |
| *官方博客中的 1F1B 示意图* | *基于源码逻辑绘制的实际调度图* |

---