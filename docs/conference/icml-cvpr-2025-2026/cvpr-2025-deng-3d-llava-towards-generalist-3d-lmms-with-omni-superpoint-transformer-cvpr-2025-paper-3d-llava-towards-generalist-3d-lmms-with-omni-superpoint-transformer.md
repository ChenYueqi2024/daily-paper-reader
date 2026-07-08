---
title: "3D-LLaVA: Towards Generalist 3D LMMs with Omni Superpoint Transformer"
title_zh: "3D-LLaVA: 朝向通用3D大型多模态模型及全能超点变压器"
authors: "Deng, Jiajun, He, Tianyu, Jiang, Li, Wang, Tianyu, Dayoub, Feras, Reid, Ian"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Deng_3D-LLaVA_Towards_Generalist_3D_LMMs_with_Omni_Superpoint_Transformer_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 3D大型多模态模型用于场景理解
tldr: 现有3D LMMs依赖复杂流水线。3D-LLaVA采用极简设计，仅输入点云，通过Omni Superpoint Transformer实现细粒度3D场景理解与推理。在多个基准上取得优异结果，推动了通用3D LMM的发展。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有3D LMMs流水线复杂，缺乏通用性。
method: 采用Omni Superpoint Transformer，仅以点云作为输入。
result: 在3D理解任务上表现优异。
conclusion: 简化了3D LMM设计并保持高性能。
---

## Abstract
Current 3D Large Multimodal Models (3D LMMs) have shown tremendous potential in 3D-vision-based dialogue and reasoning. However, how to further enhance 3D LMMs to achieve fine-grained scene understanding and facilitate flexible human-agent interaction remains a challenging problem. In this work, we introduce 3D-LLaVA, a simple yet highly powerful 3D LMM designed to act as an intelligent assistant in comprehending, reasoning, and interacting with the 3D world. Unlike existing top-performing methods that rely on complicated pipelines--such as offline multi-view feature extraction or additional task-specific heads--3D-LLaVA adopts a minimalist design with integrated architecture and only takes point clouds as input. At the core of 3D-LLaVA is a new Omni Superpoint Transformer (OST), which integrates three functionalities: (1) a visual feature selector that converts and selects visual tokens, (2) a visual prompt encoder that embeds interactive visual prompts into the visual token space, and (3) a referring mask decoder that produces 3D masks based on text description. This versatile OST is empowered by the hybrid pretraining to obtain perception priors and leveraged as the visual connector that bridges the 3D data to the LLM. After performing unified instruction tuning, our 3D-LLaVA reports impressive results on various benchmarks. The code and model will be released at https://github.com/djiajunustc/3D-LLaVA.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
3D大型多模态模型用于场景理解。

### 2. 核心内容
现有3D LMMs依赖复杂流水线。3D-LLaVA采用极简设计，仅输入点云，通过Omni Superpoint Transformer实现细粒度3D场景理解与推理。在多个基准上取得优异结果，推动了通用3D LMM的发展。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Deng_3D-LLaVA_Towards_Generalist_3D_LMMs_with_Omni_Superpoint_Transformer_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Deng_3D-LLaVA_Towards_Generalist_3D_LMMs_with_Omni_Superpoint_Transformer_CVPR_2025_paper.html)
