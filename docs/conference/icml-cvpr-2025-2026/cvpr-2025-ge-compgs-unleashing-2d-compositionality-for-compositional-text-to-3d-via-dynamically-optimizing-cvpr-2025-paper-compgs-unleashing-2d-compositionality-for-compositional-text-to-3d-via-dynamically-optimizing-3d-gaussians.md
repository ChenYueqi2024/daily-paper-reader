---
title: "CompGS: Unleashing 2D Compositionality for Compositional Text-to-3D via Dynamically Optimizing 3D Gaussians"
title_zh: "CompGS: 通过动态优化3D高斯释放2D组合性实现组合文本到3D"
authors: "Ge, Chongjian, Xu, Chenfeng, Ji, Yuanfeng, Peng, Chensheng, Tomizuka, Masayoshi, Luo, Ping, Ding, Mingyu, Jampani, Varun, Zhan, Wei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ge_CompGS_Unleashing_2D_Compositionality_for_Compositional_Text-to-3D_via_Dynamically_Optimizing_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 组合文本到3D生成使用3D高斯
tldr: 组合3D生成多个物体的交互具有挑战性。CompGS提出使用3D高斯泼溅，将2D组合性迁移到3D，逐实体初始化并动态优化，实现高效的组合文本到3D内容生成。实验证明该方法能生成多个物体合理交互的3D场景。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有3D生成难以处理多个物体的合理交互。
method: 从2D组合性初始化3D高斯参数，逐实体优化。
result: 生成高质量的组合3D场景。
conclusion: 扩展了3D高斯泼溅在组合场景中的应用。
---

## Abstract
Recent breakthroughs in text-guided image generation have significantly advanced the field of 3D generation. While generating a single high-quality 3D object is now feasible, generating multiple objects with reasonable interactions within a 3D space, a.k.a. compositional 3D generation, presents substantial challenges. This paper introduces CompGS, a novel generative framework that employs 3D Gaussian Splatting (GS) for efficient, compositional text-to-3D content generation. To achieve this goal, two core designs are proposed: (1) 3D Gaussians Initialization with 2D compositionality: We transfer the well-established 2D compositionality to initialize the Gaussian parameters on an entity-by-entity basis, ensuring both consistent 3D priors for each entity and reasonable interactions among multiple entities; (2) Dynamic Optimization: We propose a dynamic strategy to optimize 3D Gaussians using Score Distillation Sampling (SDS) loss. CompGS first automatically decomposes 3D Gaussians into distinct entity parts, enabling optimization at both the entity and composition levels. Additionally, CompGS optimizes across objects of varying scales by dynamically adjusting the spatial parameters of each entity, enhancing the generation of fine-grained details, particularly in smaller entities. Qualitative comparisons and quantitative evaluations on T3Bench demonstrate the effectiveness of CompGS in generating compositional 3D objects with superior image quality and semantic alignment over existing methods. CompGS can also be easily extended to progressively adding 3D objects, facilitating complex scene generation. We hope CompGS will provide new insights to the compositional 3D generation.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
组合文本到3D生成使用3D高斯。

### 2. 核心内容
组合3D生成多个物体的交互具有挑战性。CompGS提出使用3D高斯泼溅，将2D组合性迁移到3D，逐实体初始化并动态优化，实现高效的组合文本到3D内容生成。实验证明该方法能生成多个物体合理交互的3D场景。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Ge_CompGS_Unleashing_2D_Compositionality_for_Compositional_Text-to-3D_via_Dynamically_Optimizing_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Ge_CompGS_Unleashing_2D_Compositionality_for_Compositional_Text-to-3D_via_Dynamically_Optimizing_CVPR_2025_paper.html)
