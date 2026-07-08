---
title: "Inst3D-LMM: Instance-Aware 3D Scene Understanding with Multi-modal Instruction Tuning"
title_zh: Inst3D-LMM：实例感知的3D场景理解的多模态指令调优
authors: "Yu, Hanxun, Li, Wentong, Wang, Song, Chen, Junbo, Zhu, Jianke"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yu_Inst3D-LMM_Instance-Aware_3D_Scene_Understanding_with_Multi-modal_Instruction_Tuning_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 实例感知的3D场景理解结合多模态大模型
tldr: 针对现有方法分离2D和3D特征导致理解不全面的问题，提出Inst3D-LMM统一模型，融合2D语义和3D物体属性及空间关系，在多个3D理解任务上达到先进水平，同时提升训练和推理效率。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有方法分离2D和3D特征，忽略交互和空间关系。
method: 构建实例感知的3D多模态大模型，统一编码2D和3D信息。
result: 在多个3D场景理解任务上取得最优结果。
conclusion: 融合2D-3D交互可提升3D场景理解性能。
---

## Abstract
Despite encouraging progress in 3D scene understanding, it remains challenging to develop an effective Large Multi-modal Model (LMM) that is capable of understanding and reasoning in complex 3D environments. Most previous methods typically encode 3D point and 2D image features separately, neglecting interactions between 2D semantics and 3D object properties, as well as the spatial relationships within the 3D environment. This limitation not only hinders comprehensive representations of 3D scene, but also compromises training and inference efficiency. To address these challenges, we propose a unified Instance-aware 3D Large Multi-modal Model (Inst3D-LMM) to deal with multiple 3D scene understanding tasks simultaneously. To obtain the fine-grained instance-level visual tokens, we first introduce a novel Multi-view Cross-Modal Fusion (MCMF) module to inject the multi-view 2D semantics into their corresponding 3D geometric features. For scene-level relation-aware tokens, we further present a 3D Instance Spatial Relation (3D-ISR) module to capture the intricate pairwise spatial relationships among objects. Additionally, we perform end-to-end multi-task instruction tuning simultaneously without the subsequent task-specific fine-tuning. Extensive experiments demonstrate that our approach outperforms the state-of-the-art methods across 3D scene understanding, reasoning and grounding tasks. Source code is available at: https://github.com/hanxunyu/Inst3D-LMM.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
实例感知的3D场景理解结合多模态大模型。

### 2. 核心内容
针对现有方法分离2D和3D特征导致理解不全面的问题，提出Inst3D-LMM统一模型，融合2D语义和3D物体属性及空间关系，在多个3D理解任务上达到先进水平，同时提升训练和推理效率。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Yu_Inst3D-LMM_Instance-Aware_3D_Scene_Understanding_with_Multi-modal_Instruction_Tuning_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Yu_Inst3D-LMM_Instance-Aware_3D_Scene_Understanding_with_Multi-modal_Instruction_Tuning_CVPR_2025_paper.html)
