---
title: "GenVDM: Generating Vector Displacement Maps From a Single Image"
title_zh: GenVDM：从单张图像生成向量位移图
authors: "Yang, Yuezhi, Chen, Qimin, Kim, Vladimir G., Chaudhuri, Siddhartha, Huang, Qixing, Chen, Zhiqin"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yang_GenVDM_Generating_Vector_Displacement_Maps_From_a_Single_Image_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 生成用于3D几何细节的向量位移图
tldr: 针对3D建模中精细几何细节生成的需求，提出首个单图像生成向量位移图的方法，通过多视图法向图重建，并构建学术数据集，实验显示可生成高质量部件级几何细节，辅助艺术家创作。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有方法难以生成可附加的部件级几何细节。
method: 先生成多视图法向图，再重建向量位移图。
result: 生成的位移图可无缝附着，质量优于基线。
conclusion: 向量位移图为3D细节生成提供了新解决方案。
---

## Abstract
We introduce the first method for generating Vector Displacement Maps (VDMs): parameterized, detailed geometric stamps commonly used in 3D modeling. Given a single input image, our method first generates multi-view normal maps and then reconstructs a VDM from the normals via a novel reconstruction pipeline. We also propose an efficient algorithm for extracting VDMs from 3D objects, and present the first academic VDM dataset. Compared to existing 3D generative models focusing on complete shapes, we focus on generating parts that can be seamlessly attached to shape surfaces. The method gives artists rich control over adding geometric details to a 3D shape. Experiments demonstrate that our approach outperforms existing baselines. Generating VDMs offers additional benefits, such as using 2D image editing to customize and refine 3D details.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
生成用于3D几何细节的向量位移图。

### 2. 核心内容
针对3D建模中精细几何细节生成的需求，提出首个单图像生成向量位移图的方法，通过多视图法向图重建，并构建学术数据集，实验显示可生成高质量部件级几何细节，辅助艺术家创作。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Yang_GenVDM_Generating_Vector_Displacement_Maps_From_a_Single_Image_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Yang_GenVDM_Generating_Vector_Displacement_Maps_From_a_Single_Image_CVPR_2025_paper.html)
