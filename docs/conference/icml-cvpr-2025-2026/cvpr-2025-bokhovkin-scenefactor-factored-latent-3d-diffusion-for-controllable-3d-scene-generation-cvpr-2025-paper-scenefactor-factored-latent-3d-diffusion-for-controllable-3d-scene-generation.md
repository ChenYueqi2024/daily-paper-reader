---
title: "SceneFactor: Factored Latent 3D Diffusion for Controllable 3D Scene Generation"
title_zh: SceneFactor：用于可控3D场景生成的分解潜在3D扩散
authors: "Bokhovkin, Aleksey, Meng, Quan, Tulsiani, Shubham, Dai, Angela"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Bokhovkin_SceneFactor_Factored_Latent_3D_Diffusion_for_Controllable_3D_Scene_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 通过分解潜在扩散实现可控3D场景生成
tldr: 针对大规模3D场景生成难以精细控制的问题，提出SceneFactor，利用分解扩散在语义和几何潜空间上生成任意大小场景，并通过语义3D框代理实现局部编辑（增删改），实验显示在可控性和保真度上优于现有方法。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 文本引导场景生成缺乏局部编辑能力。
method: 分解扩散生成语义和几何潜空间，使用3D框代理进行编辑。
result: 实现高质量且可控的大规模3D场景生成。
conclusion: 分解扩散可提升3D场景生成的可控性。
---

## Abstract
We present SceneFactor, a diffusion-based approach for large-scale 3D scene generation that enables controllable generation and effortless editing. SceneFactor enables text-guided 3D scene synthesis through our factored diffusion formulation, leveraging latent semantic and geometric manifolds for generation of arbitrary-sized 3D scenes. While text input enables easy, controllable generation, text guidance remains imprecise for intuitive, localized editing and manipulation of the generated 3D scenes. Our factored semantic diffusion generates a proxy semantic space composed of semantic 3D boxes that enables controllable editing of generated scenes by adding, removing, changing the size of the semantic 3D proxy boxes that guides high-fidelity, consistent 3D geometric editing. Extensive experiments demonstrate that our approach enables high-fidelity 3D scene synthesis with effective controllable editing through our factored diffusion approach.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
通过分解潜在扩散实现可控3D场景生成。

### 2. 核心内容
针对大规模3D场景生成难以精细控制的问题，提出SceneFactor，利用分解扩散在语义和几何潜空间上生成任意大小场景，并通过语义3D框代理实现局部编辑（增删改），实验显示在可控性和保真度上优于现有方法。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Bokhovkin_SceneFactor_Factored_Latent_3D_Diffusion_for_Controllable_3D_Scene_Generation_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Bokhovkin_SceneFactor_Factored_Latent_3D_Diffusion_for_Controllable_3D_Scene_Generation_CVPR_2025_paper.html)
