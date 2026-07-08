---
title: "SAR3D: Autoregressive 3D Object Generation and Understanding via Multi-scale 3D VQVAE"
title_zh: "SAR3D: 通过多尺度3D VQVAE实现自回归3D物体生成与理解"
authors: "Chen, Yongwei, Lan, Yushi, Zhou, Shangchen, Wang, Tengfei, Pan, Xingang"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_SAR3D_Autoregressive_3D_Object_Generation_and_Understanding_via_Multi-scale_3D_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 自回归3D物体生成与理解
tldr: 自回归方法在3D领域探索不足。SAR3D提出多尺度3D VQVAE对3D物体进行token化，通过预测下一尺度表示实现高效生成和详细理解。实验表明其显著缩短生成时间，同时保持高质量，推进自回归模型在3D任务中的应用。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1797, \"height\": 280, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1815, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1803, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1622, \"height\": 654, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1804, \"height\": 470, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1790, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1761, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 889, \"height\": 506, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-sar3d-autoregressive-3d-object-generation-and-understanding-via-multi-scale-3d-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1618, \"height\": 541, \"label\": \"Table\"}]"
motivation: 自回归方法在3D物体生成和理解中应用有限。
method: 采用多尺度3D VQVAE token化，逐尺度预测自回归生成。
result: 生成时间大幅缩短，同时支持详细理解。
conclusion: 展示了自回归模型在3D领域的潜力。
---

## Abstract
Autoregressive models have demonstrated remarkable success across various fields, from large language models (LLMs) to large multimodal models (LMMs) and 2D content generation, moving closer to artificial general intelligence (AGI). Despite these advances, applying autoregressive approaches to 3D object generation and understanding remains largely unexplored. This paper introduces Scale AutoRegressive 3D (SAR3D), a novel framework that leverages a multi-scale 3D vector-quantized variational autoencoder (VQVAE) to tokenize 3D objects for efficient autoregressive generation and detailed understanding. By predicting the next scale in a multi-scale latent representation instead of the next single token, SAR3D reduces generation time significantly, achieving fast 3D object generation in just 0.82 seconds on an A6000 GPU. Additionally, given the tokens enriched with hierarchical 3D-aware information, we finetune a pretrained LLM on them, enabling multimodal comprehension of 3D content.Our experiments show that SAR3D surpasses current 3D generation methods in both speed and quality and allows LLMs to interpret and caption 3D models comprehensively.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
自回归3D物体生成与理解。

### 2. 核心内容
自回归方法在3D领域探索不足。SAR3D提出多尺度3D VQVAE对3D物体进行token化，通过预测下一尺度表示实现高效生成和详细理解。实验表明其显著缩短生成时间，同时保持高质量，推进自回归模型在3D任务中的应用。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Chen_SAR3D_Autoregressive_3D_Object_Generation_and_Understanding_via_Multi-scale_3D_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Chen_SAR3D_Autoregressive_3D_Object_Generation_and_Understanding_via_Multi-scale_3D_CVPR_2025_paper.html)
