---
layout: post
title: Enhancing LLM Planning Capabilities through Intrinsic Self-Critique
---

[[pdf](https://arxiv.org/pdf/2512.24103)]

## 个人思考

大模型幻觉现象的产生，很大程度上归因于其内在自我评价与验证机制的缺失。因此，探索大模型如何进行有效的自我批判（Self-Critique），并构建一套严密的输出质量评估体系，是提升模型逻辑可靠性、解决复杂规划问题的关键科研方向。

## 论文方案

论文提出了一种大模型如何实现"自我批判"的方案。文中最后有prompt的template，方案归纳如下：
1. 设计Prompt，让大模型针对Planning任务输出plan
2. 上述的plan，给出验证规则和通过条件，让大模型自行验证plan是正确、错误还是无法达到通过条件。
3. 将不正确的plan作为fewshot例子，加入到大模型上下文中，重复1，直到输出的plan被验证通过或者达到迭代次数上限。

## 对比方法

论文中四种方案的对比：No-Critique, Self-Critique, Self-{Critique+Consistency}, and Oracle。其中Oracle（先知）即存在验证器可以从外部引入工具来判断模型输出plan的正确性。Self-consistency可以参考[文章](https://arxiv.org/pdf/2203.11171)。Self-{Critique+Consistency}基本上可以逼近Oracle。
