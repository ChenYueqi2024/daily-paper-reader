---
title: "3DTopia-XL: Scaling High-quality 3D Asset Generation via Primitive Diffusion"
title_zh: 3DTopia-XL：通过原始扩散扩展高质量3D资产生成
authors: "Chen, Zhaoxi, Tang, Jiaxiang, Dong, Yuhao, Cao, Ziang, Hong, Fangzhou, Lan, Yushi, Wang, Tengfei, Xie, Haozhe, Wu, Tong, Saito, Shunsuke, Pan, Liang, Lin, Dahua, Liu, Ziwei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_3DTopia-XL_Scaling_High-quality_3D_Asset_Generation_via_Primitive_Diffusion_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 通过原始扩散扩展高质量3D资产生成
tldr: 针对现有3D生成模型优化速度慢、几何保真度低且缺乏PBR资产的问题，提出3DTopia-XL，采用基于原始表示的PrimX编码形状、反照率和材质，结合扩散框架在大规模数据上训练，生成高质量高分辨率PBR资产。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1806, \"height\": 912, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1797, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 329, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1809, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1803, \"height\": 1159, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 867, \"height\": 345, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 861, \"height\": 712, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 504, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-3dtopia-xl-scaling-high-quality-3d-asset-generation-via-primitive-diffusion-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 336, \"height\": 176, \"label\": \"Table\"}]"
motivation: 现有方法速度慢、几何保真度低且缺少PBR资产。
method: 提出PrimX表示和基于原始扩散的生成框架。
result: 生成高分辨率PBR资产，质量显著优于基线。
conclusion: 原始扩散可有效扩展高质量3D资产生成。
---

## Abstract
The increasing demand for high-quality 3D assets across various industries necessitates efficient and automated 3D content creation. Despite recent advancements in 3D generative models, existing methods still face challenges with optimization speed, geometric fidelity, and the lack of assets for physically based rendering (PBR). In this paper, we introduce 3DTopia-XL, a scalable native 3D generative model designed to overcome these limitations. 3DTopia-XL leverages a novel primitive-based 3D representation, PrimX, which encodes detailed shape, albedo, and material field into a compact tensorial format, facilitating the modeling of high-resolution geometry with PBR assets. On top of the novel representation, we propose a generative framework based on Diffusion Transformer (DiT), which comprises 1) Primitive Patch Compression, 2) and Latent Primitive Diffusion. 3DTopia-XL learns to generate high-quality 3D assets from textual or visual inputs. Extensive qualitative and quantitative experiments are conducted to demonstrate that 3DTopia-XL significantly outperforms existing methods in generating high-quality 3D assets with fine-grained textures and materials, efficiently bridging the quality gap between generative models and real-world applications.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过原始扩散扩展高质量3D资产生成。

### 2. 核心内容
针对现有3D生成模型优化速度慢、几何保真度低且缺乏PBR资产的问题，提出3DTopia-XL，采用基于原始表示的PrimX编码形状、反照率和材质，结合扩散框架在大规模数据上训练，生成高质量高分辨率PBR资产。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Chen_3DTopia-XL_Scaling_High-quality_3D_Asset_Generation_via_Primitive_Diffusion_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Chen_3DTopia-XL_Scaling_High-quality_3D_Asset_Generation_via_Primitive_Diffusion_CVPR_2025_paper.html)
