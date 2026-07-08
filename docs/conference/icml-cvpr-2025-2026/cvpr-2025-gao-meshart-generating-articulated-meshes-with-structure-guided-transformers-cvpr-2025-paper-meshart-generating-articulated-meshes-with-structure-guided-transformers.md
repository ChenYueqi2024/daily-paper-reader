---
title: "MeshArt: Generating Articulated Meshes with Structure-Guided Transformers"
title_zh: MeshArt：基于结构引导Transformer生成关节网格
authors: "Gao, Daoyi, Siddiqui, Yawar, Li, Lei, Dai, Angela"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Gao_MeshArt_Generating_Articulated_Meshes_with_Structure-Guided_Transformers_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 基于Transformer的关节3D网格生成
tldr: 针对可动3D物体生成中关节结构和网格拓扑保持困难的问题，本文提出MeshArt，采用分层Transformer逐部分生成关节网格。先预测物体关节结构，再基于结构合成各部件网格面，以量化三角嵌入序列建模。生成结果类手工3D模型，干净且紧凑。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有方法难以生成既具关节结构又保持规则网格拓扑的3D模型。
method: 分层Transformer先预测关节结构，再依结构逐部分生成网格面。
result: 生成具有清晰关节和紧凑几何的3D网格，质量堪比手工模型。
conclusion: 结构引导的分层生成可有效处理关节物体复杂建模。
---

## Abstract
Articulated 3D object generation is fundamental for creating realistic, functional, and interactable virtual assets which are not simply static. We introduce MeshArt, a hierarchical transformer-based approach to generate articulated 3D meshes with clean, compact geometry, reminiscent of human-crafted 3D models. We approach articulated mesh generation in a part-by-part fashion across two stages.First, we generate a high-level articulation-aware object structure; then, based on this structural information, we synthesize each part's mesh faces. Key to our approach is modeling both articulation structures and part meshes as sequences of quantized triangle embeddings, leading to a unified hierarchical framework with transformers for autoregressive generation.Object part structures are first generated as their bounding primitives and articulation modes; a second transformer, guided by these articulation structures, then generates each part's mesh triangles.To ensure coherency among generated parts, we introduce structure-guided conditioning that also incorporates local part mesh connectivity.MeshArt shows significant improvements over state of the art, with 57.1% improvement in structure coverage and a 209-point improvement in mesh generation FID.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
基于Transformer的关节3D网格生成。

### 2. 核心内容
针对可动3D物体生成中关节结构和网格拓扑保持困难的问题，本文提出MeshArt，采用分层Transformer逐部分生成关节网格。先预测物体关节结构，再基于结构合成各部件网格面，以量化三角嵌入序列建模。生成结果类手工3D模型，干净且紧凑。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Gao_MeshArt_Generating_Articulated_Meshes_with_Structure-Guided_Transformers_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Gao_MeshArt_Generating_Articulated_Meshes_with_Structure-Guided_Transformers_CVPR_2025_paper.html)
