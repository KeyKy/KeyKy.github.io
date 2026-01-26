---
layout: post
title: 数据管线（闲暇调研中）
---

## 背景

在大语言模型（LLM）的开发过程中，业界已经达成共识：“数据质量决定了模型的上限”。随着模型参数量进入千亿级，简单的、无启发式的规则过滤的Python脚本已无法满足高性能需求。在 LLM 时代之前，大规模数据处理主要依赖基于 Hadoop 生态的 MapReduce 或基于数据仓库的 Hive (HQL)。虽然这些方案在处理结构化数据时非常成熟，但在面对非结构化大模型语料时，存在明显的短板。

## 可调研的方案

1. [data-juicer](https://github.com/datajuicer/data-juicer)
2. [DataFlow](https://github.com/OpenDCAI/DataFlow)
3. [Curator](https://github.com/NVIDIA-NeMo/Curator)