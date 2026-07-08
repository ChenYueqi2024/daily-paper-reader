---
title: High-fidelity 3D Object Generation from Single Image with RGBN-Volume Gaussian Reconstruction Model
title_zh: 基于RGBN体积高斯重建模型的高保真单图3D物体生成
authors: "Shen, Yiyang, Zhou, Kun, Wang, He, Yang, Yin, Shao, Tianjia"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Shen_High-fidelity_3D_Object_Generation_from_Single_Image_with_RGBN-Volume_Gaussian_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 基于高斯泼溅的单图3D物体生成
tldr: 针对单视图3D高斯生成中几何模糊和结构缺失导致失真模糊的问题，本文提出GS-RGBN，利用RGBN体积高斯重建模型，通过结构化3D表示提高生成质量。从单张图片输入即可重建高保真3D物体。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有单视图3D高斯生成方法因几何模糊和缺乏结构导致效果差。
method: 提出RGBN体积高斯重建模型，引入结构化3D表示解决几何不一致。
result: 在多个数据集上生成高保真3D物体，优于现有方法。
conclusion: 结构化3D表示可提升单视图生成的一致性和质量。
---

## Abstract
Recently single-view 3D generation via Gaussian splatting has emerged and developed quickly. They learn 3D Gaussians from 2D RGB images generated from pre-trained multi-view diffusion (MVD) models, and have shown a promising avenue for 3D generation through a single image. Despite the current progress, these methods still suffer from the inconsistency jointly caused by the geometric ambiguity in the 2D images, and the lack of structure of 3D Gaussians, leading to distorted and blurry 3D object generation. In this paper, we propose to fix these issues by GS-RGBN, a new RGBN-volume Gaussian Reconstruction Model designed to generate high-fidelity 3D objects from single-view images. Our key insight is a structured 3D representation can simultaneously mitigate the afore-mentioned two issues. To this end, we propose a novel hybrid Voxel-Gaussian representation, where a 3D voxel representation contains explicit 3D geometric information, eliminating the geometric ambiguity from 2D images. It also structures Gaussians during learning so that the optimization tends to find better local optima. Our 3D voxel representation is obtained by a fusion module that aligns RGB features and surface normal features, both of which can be estimated from 2D images. Extensive experiments demonstrate the superiority of our methods over prior works in terms of high-quality reconstruction results, robust generalization, and good efficiency.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
基于高斯泼溅的单图3D物体生成。

### 2. 核心内容
针对单视图3D高斯生成中几何模糊和结构缺失导致失真模糊的问题，本文提出GS-RGBN，利用RGBN体积高斯重建模型，通过结构化3D表示提高生成质量。从单张图片输入即可重建高保真3D物体。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Shen_High-fidelity_3D_Object_Generation_from_Single_Image_with_RGBN-Volume_Gaussian_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Shen_High-fidelity_3D_Object_Generation_from_Single_Image_with_RGBN-Volume_Gaussian_CVPR_2025_paper.html)
