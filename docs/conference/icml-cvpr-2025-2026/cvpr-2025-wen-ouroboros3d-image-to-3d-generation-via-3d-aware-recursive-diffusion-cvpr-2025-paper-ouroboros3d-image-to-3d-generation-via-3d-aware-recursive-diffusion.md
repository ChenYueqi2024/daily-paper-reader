---
title: "Ouroboros3D: Image-to-3D Generation via 3D-aware Recursive Diffusion"
title_zh: Ouroboros3D：通过3D感知递归扩散进行图像到3D生成
authors: "Wen, Hao, Huang, Zehuan, Wang, Yaohui, Chen, Xinyuan, Sheng, Lu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wen_Ouroboros3D_Image-to-3D_Generation_via_3D-aware_Recursive_Diffusion_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 通过带反馈的递归扩散从图像生成3D
tldr: 针对图像到3D方法因分阶段处理导致的3D不一致和域差距问题，提出端到端的Ouroboros3D，通过递归扩散过程融合多视图生成与重建，实验显示在标准基准上取得更优的3D一致性和保真度。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 分阶段方法导致3D不一致和域差距。
method: 将多视图生成和3D重建整合进递归扩散，引入反馈机制。
result: 在多视图一致性和重建质量上超越基线。
conclusion: 递归扩散可端到端提升图像到3D生成质量。
---

## Abstract
Existing image-to-3D creation methods typically split the task into two individual stage: multi-view image generation and 3D reconstruction, leading to two main limitations: (1) In multi-view generation stage, the multi-view generated images present a challenge to preserving 3D consistency;; (2) In 3D reconstruction stage, there is a domain gap between real training data and generated multi-view input during inference. To address these issues, we propose Ouroboros3D, end-to-end trainable framework that integrates multi-view generation and 3D reconstruction into a recursive diffusion process through feedback mechanism.Our framework operates through iterative cycles where each cycle consists of a denoising process and a reconstruction step.By incorporating a 3D-aware feedback mechanism, our multi-view generative model leverages the explicit 3D geometric information (e.g. texture, position) from the feedback of reconstruction results of the previous process as conditions, thus modeling consistency at the 3D geometric level. Furthermore, through joint training of both the multi-view generative and reconstruction models, we alleviate reconstruction stage domain gap and enable mutual enhancement within the recursive process. Experimental results demonstrate that Ouroboros3D outperforms methods that treat these stages separately and those that combine them only during inference, achieving superior multi-view consistency and producing 3D models with higher geometric realism.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过带反馈的递归扩散从图像生成3D。

### 2. 核心内容
针对图像到3D方法因分阶段处理导致的3D不一致和域差距问题，提出端到端的Ouroboros3D，通过递归扩散过程融合多视图生成与重建，实验显示在标准基准上取得更优的3D一致性和保真度。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Wen_Ouroboros3D_Image-to-3D_Generation_via_3D-aware_Recursive_Diffusion_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Wen_Ouroboros3D_Image-to-3D_Generation_via_3D-aware_Recursive_Diffusion_CVPR_2025_paper.html)
