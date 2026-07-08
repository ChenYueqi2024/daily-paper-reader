---
title: "PartGen: Part-level 3D Generation and Reconstruction with Multi-view Diffusion Models"
title_zh: "PartGen: 基于多视图扩散模型的部分级3D生成与重建"
authors: "Chen, Minghao, Shapovalov, Roman, Laina, Iro, Monnier, Tom, Wang, Jianyuan, Novotny, David, Vedaldi, Andrea"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_PartGen_Part-level_3D_Generation_and_Reconstruction_with_Multi-view_Diffusion_Models_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 部分级3D生成与重建
tldr: 现有3D资产作为单个实体缺乏有意义结构。PartGen提出多视图扩散模型，先提取部分分割，再生成每个部分，从而从文本、图像或无结构3D输入创建具有独立可操作部分的3D物体。实验验证了生成结构的合理性和可控性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 3D资产通常缺乏有意义的部件级结构。
method: 利用多视图扩散模型进行部分分割和逐部分生成。
result: 生成具有独立可操作部分的3D物体。
conclusion: 弥合了3D生成与实用性结构需求之间的差距。
---

## Abstract
Text- or image-to-3D generators and 3D scanners can now produce 3D assets with high-quality shapes and textures, but as single, fused entities lacking meaningful structure. In contrast, most applications and creative workflows require 3D assets to be composed of distinct, meaningful parts that can be independently manipulated. To bridge this gap, we introduce PartGen, a novel approach for generating, from text, images, or unstructured 3D objects, 3D objects composed of meaningful parts. Our method leverages a multi-view diffusion model to extract plausible and view-consistent part segmentations from multiple views of a 3D object, dividing it into meaningful components. A second multi-view diffusion model then processes each part individually, filling in occlusions and generating completed views, which are subsequently passed to a 3D reconstruction network. The completion process ensures that the reconstructed parts integrate cohesively by considering the context of the entire object, compensating for missing information caused by occlusions and, in extreme cases, hallucinating entirely invisible parts based on contextual cues. We evaluate PartGen on both generated and real 3D assets, demonstrating significant improvements over segmentation and part completion baselines. We also showcase downstream applications such as text-guided 3D part editing.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
部分级3D生成与重建。

### 2. 核心内容
现有3D资产作为单个实体缺乏有意义结构。PartGen提出多视图扩散模型，先提取部分分割，再生成每个部分，从而从文本、图像或无结构3D输入创建具有独立可操作部分的3D物体。实验验证了生成结构的合理性和可控性。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Chen_PartGen_Part-level_3D_Generation_and_Reconstruction_with_Multi-view_Diffusion_Models_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Chen_PartGen_Part-level_3D_Generation_and_Reconstruction_with_Multi-view_Diffusion_Models_CVPR_2025_paper.html)
