---
title: "Kiss3DGen: Repurposing Image Diffusion Models for 3D Asset Generation"
title_zh: Kiss3DGen：重用图像扩散模型进行3D资产生成
authors: "Lin, Jiantao, Yang, Xin, Chen, Meixi, Xu, Yingjie, Yan, Dongyu, Wu, Leyi, Xu, Xinli, Xu, Lie, Zhang, Shunsi, Chen, Ying-Cong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Lin_Kiss3DGen_Repurposing_Image_Diffusion_Models_for_3D_Asset_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 重用2D图像扩散模型生成3D资产
tldr: 针对3D生成依赖大规模3D数据的问题，本文提出Kiss3DGen，通过微调2D图像扩散模型生成“3D捆绑图像”（多视图与法线图），进而重建3D网格并纹理化。该方法无需3D训练数据，实现高效3D资产生成、编辑与增强。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 高质量3D数据稀缺，现有方法依赖大规模3D资产训练。
method: 微调2D扩散模型生成多视图和法线图，利用法线图重建3D网格。
result: 仅用2D数据即可生成多样化3D资产，泛化性强。
conclusion: 2D先验可有效迁移至3D任务，降低数据依赖。
---

## Abstract
Diffusion models have achieved great success in generating 2D images. However, the quality and generalizability of 3D content generation remain limited. State-of-the-art methods often require large-scale 3D assets for training, which are challenging to collect. In this work, we introduce Kiss3DGen (Keep It Simple and Straightforward in 3D Generation), an efficient framework for generating, editing, and enhancing 3D objects by repurposing a well-trained 2D image diffusion model for 3D generation. Specifically, we fine-tune a diffusion model to generate "3D Bundle Image", a tiled representation composed of multi-view images and their corresponding normal maps. The normal maps are then used to reconstruct a 3D mesh, and the multi-view images provide texture mapping, resulting in a complete 3D model. This simple method effectively transforms the 3D generation problem into a 2D image generation task, maximizing the utilization of knowledge in pretrained diffusion models. Furthermore, we demonstrate that our Kiss3DGen model is compatible with various diffusion model techniques, enabling advanced features such as 3D editing, mesh and texture enhancement, etc. Through extensive experiments, we demonstrate the effectiveness of our approach, showcasing its ability to produce high-quality 3D models efficiently.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
重用2D图像扩散模型生成3D资产。

### 2. 核心内容
针对3D生成依赖大规模3D数据的问题，本文提出Kiss3DGen，通过微调2D图像扩散模型生成“3D捆绑图像”（多视图与法线图），进而重建3D网格并纹理化。该方法无需3D训练数据，实现高效3D资产生成、编辑与增强。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Lin_Kiss3DGen_Repurposing_Image_Diffusion_Models_for_3D_Asset_Generation_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Lin_Kiss3DGen_Repurposing_Image_Diffusion_Models_for_3D_Asset_Generation_CVPR_2025_paper.html)
