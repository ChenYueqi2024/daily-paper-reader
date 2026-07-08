---
title: "Hash3D: Training-free Acceleration for 3D Generation"
title_zh: Hash3D：3D生成的无训练加速
authors: "Yang, Xingyi, Liu, Songhua, Wang, Xinchao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yang_Hash3D_Training-free_Acceleration_for_3D_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 通过特征哈希实现3D生成的无训练加速
tldr: 针对3D生成中SDS优化过程缓慢的问题，提出无需训练的Hash3D，通过自适应网格哈希重用附近时间步和视角的冗余特征图，大幅加速生成过程且保持质量，实验显示可加速数倍。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 3D SDS优化过程计算开销大、效率低。
method: 利用自适应哈希对冗余特征图进行重用。
result: 在保持质量前提下显著加速3D生成。
conclusion: 特征哈希可有效加速3D生成而无须训练。
---

## Abstract
The quality of 3D generative modeling has been notably improved by the adoption of 2D diffusion models. Despite this progress, the cumbersome optimization process per sepresents a critical problem to efficiency. In this paper, we introduce Hash3D, a universal acceleration for 3D score distillation sampling (SDS) without model training.Central to Hash3D is the observation that images rendered from similar camera positions and diffusion time-steps often have redundant feature maps. By hashing and reusing these feature maps across nearby timesteps and camera angles, Hash3D eliminates unnecessary calculations. We implement this through an adaptive grid-based hashing. As a result, it largely speeds up the process of 3D generation. Surprisingly, this feature-sharing mechanism not only makes generation faster but also improves the smoothness and view consistency of the synthesized 3D objects. Our experiments covering 5 text-to-3D and 3 image-to-3D models, demonstrate Hash3D's versatility to speed up optimization, enhancing efficiency by 1.5~ 4x. Additionally, Hash3D's integration with 3D Gaussian splatting largely speeds up 3D model creation, reducing text-to-3D conversion to about 10 minutes and image-to-3D conversion to 30 seconds. The project page is https://adamdad.github.io/hash3D/.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过特征哈希实现3D生成的无训练加速。

### 2. 核心内容
针对3D生成中SDS优化过程缓慢的问题，提出无需训练的Hash3D，通过自适应网格哈希重用附近时间步和视角的冗余特征图，大幅加速生成过程且保持质量，实验显示可加速数倍。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Yang_Hash3D_Training-free_Acceleration_for_3D_Generation_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Yang_Hash3D_Training-free_Acceleration_for_3D_Generation_CVPR_2025_paper.html)
