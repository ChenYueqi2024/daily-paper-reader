---
title: "Prometheus: 3D-Aware Latent Diffusion Models for Feed-Forward Text-to-3D Scene Generation"
title_zh: "Prometheus: 用于前馈文本到3D场景生成的3D感知潜在扩散模型"
authors: "Yang, Yuanbo, Shao, Jiahao, Li, Xinyang, Shen, Yujun, Geiger, Andreas, Liao, Yiyi"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yang_Prometheus_3D-Aware_Latent_Diffusion_Models_for_Feed-Forward_Text-to-3D_Scene_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 潜在扩散模型进行文本到3D场景生成
tldr: 现有文本到3D生成速度慢或质量低。Prometheus提出3D感知潜在扩散模型，利用RGB-D潜在空间解耦外观与几何，基于预训练图像模型实现前馈生成。在秒级内生成高质量3D物体和场景，展示了极快的速度和良好的泛化性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1512, \"height\": 1321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1821, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1723, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1729, \"height\": 553, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1321, \"height\": 347, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 837, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1727, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1733, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-prometheus-3d-aware-latent-diffusion-models-for-feed-forward-text-to-3d-scene-generation-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 840, \"height\": 267, \"label\": \"Table\"}]"
motivation: 文本到3D生成需要快速且高质量的方案。
method: 采用3D感知潜在扩散，RGB-D潜在空间，基于预训练图像模型。
result: 在秒级内生成高质量3D物体和场景。
conclusion: 实现了高效且通用的文本到3D生成。
---

## Abstract
In this work, we introduce Prometheus, a 3D-aware latent diffusion model for text-to-3D generation at both object and scene levels in seconds. We formulate 3D scene generation as multi-view, feed-forward, pixel-aligned 3D Gaussian generation within the latent diffusion paradigm. To ensure generalizability, we build our model upon pre-trained text-to-image generation model with only minimal adjustments and further train it using a large number of images from both single-view and multi-view datasets. Furthermore, we introduce an RGB-D latent space into 3D Gaussian generation to disentangle appearance and geometry information, enabling efficient feed-forward generation of 3D Gaussians with better fidelity and geometry. Extensive experimental results demonstrate the effectiveness of our method in both feed-forward 3D Gaussian reconstruction and text-to-3D generation.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
潜在扩散模型进行文本到3D场景生成。

### 2. 核心内容
现有文本到3D生成速度慢或质量低。Prometheus提出3D感知潜在扩散模型，利用RGB-D潜在空间解耦外观与几何，基于预训练图像模型实现前馈生成。在秒级内生成高质量3D物体和场景，展示了极快的速度和良好的泛化性。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Yang_Prometheus_3D-Aware_Latent_Diffusion_Models_for_Feed-Forward_Text-to-3D_Scene_Generation_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Yang_Prometheus_3D-Aware_Latent_Diffusion_Models_for_Feed-Forward_Text-to-3D_Scene_Generation_CVPR_2025_paper.html)
