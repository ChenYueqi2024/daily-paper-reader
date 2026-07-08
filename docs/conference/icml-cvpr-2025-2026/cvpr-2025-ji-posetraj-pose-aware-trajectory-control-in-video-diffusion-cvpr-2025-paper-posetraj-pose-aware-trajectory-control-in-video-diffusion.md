---
title: "PoseTraj: Pose-Aware Trajectory Control in Video Diffusion"
title_zh: "PoseTraj: 视频扩散中的姿态感知轨迹控制"
authors: "Ji, Longbin, Zhong, Lei, Wei, Pengfei, Li, Changjian"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ji_PoseTraj_Pose-Aware_Trajectory_Control_in_Video_Diffusion_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 从2D轨迹生成3D对齐运动
tldr: 现有轨迹引导视频生成缺乏对6D姿态变化的3D理解。PoseTraj提出姿态感知视频拖拽模型，通过两阶段预训练和3D边界框监督，从2D轨迹生成3D对齐运动。在合成数据集上实验表明，该方法能有效处理大范围旋转，提升视频生成中的3D一致性。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有轨迹引导视频生成在6D姿态变化和大范围旋转下缺乏3D理解。
method: 提出两阶段姿态感知预训练框架，利用3D边界框作为中间监督。
result: 生成3D对齐运动，在旋转轨迹上表现准确。
conclusion: 增强视频扩散模型的3D姿态感知能力。
---

## Abstract
Recent advancements in trajectory-guided video generation have achieved notable progress. However, existing models still face challenges in generating object motions with potentially changing 6D poses under wide-range rotations, due to limited 3D understanding. To address this problem, we introduce PoseTraj, a pose-aware video dragging model for generating 3D-aligned motion from 2D trajectories. Our method adopts a novel two-stage pose-aware pretraining framework, improving 3D understanding across diverse trajectories. Specifically, we propose a large-scale synthetic dataset PoseTraj-10k, containing 10k videos of objects following rotational trajectories, and enhance the model perception of object pose changes by incorporating 3D bounding boxes as intermediate supervision signals. Following this, we fine-tune the trajectory-controlling module on real-world videos, applying an additional camera-disentanglement module to further refine motion accuracy. Experiments on various benchmark datasets demonstrate that our method not only excels in 3D pose-aligned dragging for rotational trajectories but also outperforms existing baselines in trajectory accuracy and video quality.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
从2D轨迹生成3D对齐运动。

### 2. 核心内容
现有轨迹引导视频生成缺乏对6D姿态变化的3D理解。PoseTraj提出姿态感知视频拖拽模型，通过两阶段预训练和3D边界框监督，从2D轨迹生成3D对齐运动。在合成数据集上实验表明，该方法能有效处理大范围旋转，提升视频生成中的3D一致性。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Ji_PoseTraj_Pose-Aware_Trajectory_Control_in_Video_Diffusion_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Ji_PoseTraj_Pose-Aware_Trajectory_Control_in_Video_Diffusion_CVPR_2025_paper.html)
