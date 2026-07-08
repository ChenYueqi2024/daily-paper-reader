---
title: "CraftsMan3D: High-fidelity Mesh Generation with 3D Native Diffusion and Interactive Geometry Refiner"
title_zh: CraftsMan3D：基于3D原生扩散与交互式几何优化的高保真网格生成
authors: "Li, Weiyu, Liu, Jiarui, Yan, Hongyu, Chen, Rui, Liang, Yixun, Chen, Xuelin, Tan, Ping, Long, Xiaoxiao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_CraftsMan3D_High-fidelity_Mesh_Generation_with_3D_Native_Diffusion_and_Interactive_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 基于3D原生扩散的高保真网格生成
tldr: 针对现有3D生成中网格拓扑不规则、自遮挡和用户编辑困难的问题，本文提出CraftsMan3D，采用3D原生扩散模型生成完整几何，再通过交互式几何优化器细化表面细节。该方法生成高质量规则网格，并支持用户交互编辑。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1784, \"height\": 710, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 875, \"height\": 291, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1791, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 866, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 738, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 831, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1685, \"height\": 855, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 708, \"height\": 517, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 805, \"height\": 477, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 700, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 561, \"height\": 203, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-craftsman3d-high-fidelity-mesh-generation-with-3d-native-diffusion-and-interactive-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 690, \"height\": 235, \"label\": \"Table\"}]"
motivation: 现有3D生成方法产生不规则网格，难以编辑和集成到建模软件。
method: 提出3D原生扩散模型生成完整几何，结合交互式几何优化器细化表面。
result: 生成具有规则拓扑和细密表面的高保真网格，支持用户交互。
conclusion: 3D原生扩散与交互优化结合可提升网格质量和可用性。
---

## Abstract
We present a novel generative 3D modeling system, coined CraftsMan, which can generate high-fidelity 3D geometries with highly varied shapes, regular mesh topologies, and detailed surfaces, and, notably, allows for refining the geometry in an interactive manner. Despite the significant advancements in 3D generation, existing methods still struggle with lengthy optimization processes, self-occlusion, irregular mesh topologies, and difficulties in accommodating user edits, consequently impeding their widespread adoption and implementation in 3D modeling softwares. Our work is inspired by the craftsman, who usually roughs out the holistic figure of the work first and elaborates the surface details subsequently. Specifically, we first introduce a robust data preprocessing pipeline that utilizes visibility check and winding mumber to maximize the use of existing 3D data. Leveraging this data, we employ a 3D-native DiT model that directly models the distribution of 3D data in latent space, generating coarse geometries with regular mesh topology in seconds. Subsequently, a normal-based geometry refiner enhances local surface details, which can be applied automatically or interactively with user input. Extensive experiments demonstrate that our method achieves high efficacy in producing superior quality 3D assets compared to existing methods.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
基于3D原生扩散的高保真网格生成。

### 2. 核心内容
针对现有3D生成中网格拓扑不规则、自遮挡和用户编辑困难的问题，本文提出CraftsMan3D，采用3D原生扩散模型生成完整几何，再通过交互式几何优化器细化表面细节。该方法生成高质量规则网格，并支持用户交互编辑。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Li_CraftsMan3D_High-fidelity_Mesh_Generation_with_3D_Native_Diffusion_and_Interactive_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Li_CraftsMan3D_High-fidelity_Mesh_Generation_with_3D_Native_Diffusion_and_Interactive_CVPR_2025_paper.html)
