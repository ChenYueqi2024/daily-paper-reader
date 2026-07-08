---
title: "SpatialLLM: A Compound 3D-Informed Design towards Spatially-Intelligent Large Multimodal Models"
title_zh: "SpatialLLM: 朝向空间智能大型多模态模型的复合3D知情设计"
authors: "Ma, Wufei, Ye, Luoxin, de Melo, Celso M, Yuille, Alan, Chen, Jieneng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ma_SpatialLLM_A_Compound_3D-Informed_Design_towards_Spatially-Intelligent_Large_Multimodal_Models_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 大型多模态模型进行3D空间推理
tldr: 现有LMMs缺乏3D空间推理能力。SpatialLLM系统性地引入3D感知数据（位置、方向）和3D知觉层，训练后使模型具备高级3D空间推理能力。在多种空间推理任务上显著提升，弥补了LMMs在3D空间理解的缺陷。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 大型多模态模型缺乏3D空间推理能力。
method: 设计3D感知训练数据和3D知觉架构层。
result: 在3D空间推理任务上取得显著提升。
conclusion: 为LMMs注入空间智能提供有效途径。
---

## Abstract
Humans naturally understand 3D spatial relationships, enabling complex reasoning like predicting collisions of vehicles from different directions. Current large multimodal models (LMMs), however, lack of this capability of 3D spatial reasoning. This limitation stems from the scarcity of 3D training data and the bias in current model designs toward 2D data. In this paper, we systematically study the impact of 3D-informed data, architecture, and training setups, introducing SpatialLLM, a large multi-modal model with advanced 3D spatial reasoning abilities. To address data limitations, we develop two types of 3D-informed training datasets: (1) 3D-informed probing data focused on object's 3D location and orientation, and (2) 3D-informed conversation data for complex spatial relationships. Notably, we are the first to curate VQA data that incorporate 3D orientation relationships on real images. Furthermore, we systematically integrate these two types of training data with the architectural and training designs of LMMs, providing a roadmap for optimal design aimed at achieving superior 3D reasoning capabilities. Our SpatialLLM advances machines toward highly capable 3D-informed reasoning, surpassing GPT-4o performance by 8.7%. Our systematic empirical design and the resulting findings offer valuable insights for future research in this direction.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
大型多模态模型进行3D空间推理。

### 2. 核心内容
现有LMMs缺乏3D空间推理能力。SpatialLLM系统性地引入3D感知数据（位置、方向）和3D知觉层，训练后使模型具备高级3D空间推理能力。在多种空间推理任务上显著提升，弥补了LMMs在3D空间理解的缺陷。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Ma_SpatialLLM_A_Compound_3D-Informed_Design_towards_Spatially-Intelligent_Large_Multimodal_Models_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Ma_SpatialLLM_A_Compound_3D-Informed_Design_towards_Spatially-Intelligent_Large_Multimodal_Models_CVPR_2025_paper.html)
