---
title: "Holi-Spatial: Evolving Video Streams into Holistic 3D Spatial Intelligence"
title_zh: "Holi-Spatial: 将视频流演变为整体3D空间智能"
authors: "Yuanyuan Gao, Hao Li, Yifei Liu, Xinhao Ji, Yuning Gong, Yuanjun Liao, Fangfu Liu, Manyuan Zhang, Yuchen Yang, Dan Xu, Xue Yang, Huaxi Huang, Hongjie Zhang, Ziwei Liu, Xiao Sun, Dingwen Zhang, Zhihang Zhong"
date: 2026-04-30
pdf: "https://openreview.net/pdf/6629144b1a249059f71cb5a3e9a2b54504764588.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 从视频构建3D空间智能数据集
tldr: 现有3D理解基准依赖有限手工标注数据，可扩展性差。Holi-Spatial提出全自动管道，从原始网络视频构建大规模空间感知多模态数据集，无需人工干预。实验证明该数据集能有效缓解领域差距，为3D空间智能研究提供基础。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有3D理解基准依赖有限手工标注，可扩展性受限且存在领域差距。
method: 提出全自动数据管道，从原始视频输入构建大规模空间感知多模态数据集。
result: 首次实现无需人工干预的大规模3D空间数据集构建。
conclusion: 为3D空间智能研究提供了可扩展的数据基础。
---

## Abstract
The pursuit of spatial intelligence fundamentally relies on access to large-scale, fine-grained 3D data. However, existing approaches predominantly construct spatial understanding benchmarks by generating question–answer (QA) pairs from a limited number of manually annotated datasets, rather than systematically annotating new large-scale 3D scenes from raw web data. As a result, their scalability is severely constrained, and model performance is further hindered by domain gaps inherent in these narrowly curated datasets.
In this work, we propose \textbf{Holi-Spatial}, the first fully automated, large-scale, spatially-aware multimodal dataset, constructed from raw video inputs without human intervention, using the proposed data curation pipeline. Holi-Spatial supports multi-level spatial supervision, ranging from geometrically accurate 3D Gaussian Splatting (3DGS) reconstructions with rendered depth maps to object-level and relational semantic annotations, together with corresponding spatial Question–Answer (QA) pairs.
Following a principled and systematic pipeline, we further construct \textbf{Holi-Spatial-4M}, the first large-scale, high-quality 3D semantic dataset, containing 12K optimized 3DGS scenes, 1.3M 2D masks, 320K 3D bounding boxes, 320K instance captions, 1.2M 3D grounding instances, and 1.2M spatial QA pairs spanning diverse geometric, relational, and semantic reasoning tasks.
Holi-Spatial demonstrates exceptional performance in data curation quality, significantly outperforming existing feed-forward and per-scene optimized methods on datasets such as ScanNet, ScanNet++, and DL3DV. Furthermore, fine-tuning Vision-Language Models (VLMs) on spatial reasoning tasks using this dataset has also led to substantial improvements in model performance.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有3D空间理解基准（如ScanNet、ScanNet++、DL3DV等）主要依赖有限的手工标注数据集来生成问答（QA）对，缺乏从原始网络视频中系统化、大规模地自动标注新3D场景的能力。这导致数据扩展性严重受限，且模型性能受限于狭窄人工数据集的领域差距（domain gap）。
- **研究动机**：空间智能（Spatial Intelligence）的实现需要大规模、细粒度的3D数据支撑。现有方法无法突破人工标注的瓶颈，急需一种无需人工干预的全自动数据构建管道，以生成大规模、高质量、多模态、空间感知的数据集。
- **整体含义**：本文提出的 **Holi-Spatial** 是首个全自动的大规模空间感知多模态数据集构造方法，为3D空间智能研究提供了可扩展的数据基础，并首次实现了无需人工干预的大规模3D空间数据集构建。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出一套**全自动数据标注管道**（fully automated data curation pipeline），从原始网络视频输入出发，自动生成几何精确的3D高斯泼溅（3DGS）重建、深度图、对象级/关系级语义标注以及相应的空间问答（QA）对。整个过程无需任何人工干预。
- **关键技术细节**：
  - **视频输入→3DGS重建**：对原始视频进行3D高斯泼溅优化，获得几何精确的3D场景表示及渲染深度图。
  - **多级空间监督**：支持从像素级（深度图）、对象级（2D masks、3D bounding boxes、实例描述）、关系级（空间QA对）的多层次标注。
  - **管道流程**（文字描述）：原始视频 → 3DGS场景重建 → 自动生成2D/3D分割、检测、实例描述 → 基于空间关系自动生成QA对 → 最终得到大规模高质量数据集。
- **具体数据集产物**：Holi-Spatial-4M 包含12K优化3DGS场景、1.3M 2D masks、320K 3D边界框、320K实例描述、1.2M 3D接地实例、1.2M空间QA对（覆盖几何、关系、语义推理任务）。

## 3. 实验设计：数据集 / 场景、Benchmark、对比方法

- **使用的数据集/场景**：评估在现有3D理解基准上进行，包括 **ScanNet、ScanNet++、DL3DV** 等。
- **Benchmark**：论文未明确列出具体的评估指标，但提及在数据质量（data curation quality）上比较了现有前馈（feed-forward）方法和每场景优化（per-scene optimized）方法。
- **对比方法**：对比了现有的前馈方法（如某些基于视频的3D重建/理解方法）和每场景优化方法（如传统3D重建+手工标注）。此外，还将Holi-Spatial数据集用于微调视觉语言模型（VLMs），比较微调前后的空间推理性能。
- **实验类型**：
  - **数据质量评估**：对比不同方法生成的3D场景/标注质量。
  - **下游任务微调**：在空间推理任务上微调VLMs，评估性能提升。

## 4. 资源与算力

- **文中未明确说明**算力信息（如GPU型号、数量、训练时长等）。摘要和元数据中均未提及具体计算资源。因此无法总结此部分，需指出这一缺失。

## 5. 实验数量与充分性

- **实验数量**：论文主要进行了两类实验：（1）数据质量对比（在3个数据集上对比两种类型的方法）；（2）VLM微调实验（展示性能提升）。具体消融实验（如管道中各模块的贡献）未在摘要中提及，可能全文中有更多实验。
- **充分性判断**：从摘要看，实验覆盖了主流3D理解基准，并验证了数据集在下游任务中的有效性。但缺少消融实验细节（如不同标注级别的影响、数据规模的影响等）。对比方法虽然明确，但仅提及“显著优于”，无具体数值，客观性需审稿意见支持。总体而言，实验设计较为充分，但信息有限。

## 6. 论文的主要结论与发现

- Holi-Spatial是首个无需人工干预的全自动大规模空间感知多模态数据集构建方法。
- 构建的Holi-Spatial-4M数据集在数据质量上显著优于现有前馈和每场景优化方法（在ScanNet等基准上）。
- 使用该数据集微调视觉语言模型，在空间推理任务上带来实质性性能提升。
- 结论：该工作为3D空间智能研究提供了可扩展、高质量的数据基础，有效缓解了领域差距问题。

## 7. 优点：方法或实验设计上的亮点

- **全自动化**：首次实现从原始视频到3D空间数据集的全自动构建，摆脱人工标注瓶颈。
- **多模态多级别**：数据集包含几何（3DGS+深度）、语义（2D/3D分割、检测、描述）、推理（空间QA）多方面信息，支持多种下游任务。
- **大规模**：构建了12000个3D场景，1.2M QA对，数据量级远超现有手工标注数据集。
- **实用性**：通过微调VLM验证了数据集的实际价值，证明其能有效提升模型空间理解能力。

## 8. 不足与局限

- **实验覆盖不完整**：摘要未提供具体数值和消融实验，无法确认各模块贡献；未与其他大规模数据集（如Objaverse、3D-FUTURE等）对比。
- **偏差风险**：原始视频来源于网络，可能存在分布偏差（如场景类型、物体类别、视角偏好），且未讨论数据清洗和标注质量控制的细节。
- **应用限制**：数据集仅包含3DGS场景，需要视频输入；对于非视频数据（如单一图像或点云）可能无法直接应用。管道对视频质量要求未知。
- **算力开销**：虽然未提及，但3DGS优化+自动标注大规模数据（12K场景）可能计算成本高昂，未在论文中讨论可复现性或效率。
- **未见完整论文**：当前仅基于摘要，完整性受限。

---

（完）
