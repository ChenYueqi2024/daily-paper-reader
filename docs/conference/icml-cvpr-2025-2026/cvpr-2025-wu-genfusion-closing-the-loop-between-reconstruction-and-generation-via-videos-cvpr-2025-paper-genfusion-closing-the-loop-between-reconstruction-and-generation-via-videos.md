---
title: "GenFusion: Closing the Loop between Reconstruction and Generation via Videos"
title_zh: GenFusion：通过视频弥合3D重建与生成之间的闭环
authors: "Wu, Sibo, Xu, Congrong, Huang, Binbin, Geiger, Andreas, Chen, Anpei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wu_GenFusion_Closing_the_Loop_between_Reconstruction_and_Generation_via_Videos_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 通过视频扩散融合3D重建与生成
tldr: 针对3D重建与生成之间的条件鸿沟，本文提出GenFusion，利用重建驱动的视频扩散模型，将视频帧条件化于含伪影的RGB-D渲染，并通过循环融合管道迭代改进。该方法有效对齐3D约束与生成先验，提升新视图合成质量。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 3D重建依赖密集视图，而生成仅需少量输入，两者条件不一致。
method: 提出重建驱动的视频扩散模型和循环融合管道，交替优化重建与生成。
result: 在多种数据集上实现高质量新视图合成，有效缓解条件鸿沟。
conclusion: 视频扩散可统一重建与生成，拓展3D应用场景。
---

## Abstract
Recently, 3D reconstruction and generation have demonstrated impressive novel view synthesis results, achieving high fidelity and efficiency. However, a notable conditioning gap can be observed between these two fields, e.g. , scalable 3D scene reconstruction often requires densely captured views, whereas 3D generation typically relies on a single or no input view, which significantly limits their applications. We found that the source of this phenomenon lies in the misalignment between 3D constraints and generative priors. To address this problem, we propose a reconstruction-driven video diffusion model that learns to condition video frames on artifact-prone RGB-D renderings. Moreover, we propose a cyclical fusion pipeline that iteratively adds restoration frames from the generative model to the training set, enabling progressive expansion and addressing the viewpoint saturation limitations seen in previous reconstruction and generation pipelines. Our evaluation, including view synthesis from sparse view and masked input, validates the effectiveness of our approach.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过视频扩散融合3D重建与生成。

### 2. 核心内容
针对3D重建与生成之间的条件鸿沟，本文提出GenFusion，利用重建驱动的视频扩散模型，将视频帧条件化于含伪影的RGB-D渲染，并通过循环融合管道迭代改进。该方法有效对齐3D约束与生成先验，提升新视图合成质量。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Wu_GenFusion_Closing_the_Loop_between_Reconstruction_and_Generation_via_Videos_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Wu_GenFusion_Closing_the_Loop_between_Reconstruction_and_Generation_via_Videos_CVPR_2025_paper.html)
