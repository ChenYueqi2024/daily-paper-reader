---
title: "Eval3D: Interpretable and Fine-grained Evaluation for 3D Generation"
title_zh: Eval3D：可解释的细粒度3D生成评估
authors: "Duggal, Shivam, Hu, Yushi, Michel, Oscar, Kembhavi, Aniruddha, Freeman, William T., Smith, Noah A., Krishna, Ranjay, Torralba, Antonio, Farhadi, Ali, Ma, Wei-Chiu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Duggal_Eval3D_Interpretable_and_Fine-grained_Evaluation_for_3D_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 细粒度3D生成质量评估工具
tldr: 针对现有3D评估指标忽略几何质量或不透明的问题，提出Eval3D细粒度可解释评估工具，从几何、视觉和语义一致性等多维度评估生成资产，实验表明其与人类判断高度一致。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有3D评估指标忽略几何质量或依赖黑盒模型。
method: 建立多标准评估框架，分别评估几何、外观和一致性。
result: 评估结果与人类判断高度吻合。
conclusion: 细粒度可解释评估能更准确反映3D生成质量。
---

## Abstract
Despite the unprecedented progress in the field of 3D generation, current systems still often fail to produce high-quality 3D assets that are visually appealing and geometrically and semantically consistent across multiple viewpoints. To effectively assess the quality of the generated 3D data, there is a need for a reliable 3D evaluation tool. Unfortunately, existing 3D evaluation metrics often overlook the geometric quality of generated assets or merely rely on black-box multimodal large language models for coarse assessment. In this paper, we introduce Eval3D, a fine-grained, interpretable evaluation tool that can faithfully evaluate the quality of generated 3D assets based on various distinct yet complementary criteria. Our key observation is that many desired properties of 3D generation, such as semantic and geometric consistency, can be effectively captured by measuring the consistency among various foundation models and tools. We thus leverage a diverse set of models and tools as probes to evaluate the inconsistency of generated 3D assets across different aspects. Compared to prior work, Eval3D provides pixel-wise measurement, enables accurate 3D spatial feedback, and aligns more closely with human judgments. We comprehensively evaluate existing 3D generation models using Eval3D and highlight the limitations and challenges of current models.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
细粒度3D生成质量评估工具。

### 2. 核心内容
针对现有3D评估指标忽略几何质量或不透明的问题，提出Eval3D细粒度可解释评估工具，从几何、视觉和语义一致性等多维度评估生成资产，实验表明其与人类判断高度一致。

### 3. 对应检索需求
3D generation and understanding。

### 4. 来源与原文
- Source：CVPR-2025-Accepted
- OpenReview：[https://openaccess.thecvf.com/content/CVPR2025/html/Duggal_Eval3D_Interpretable_and_Fine-grained_Evaluation_for_3D_Generation_CVPR_2025_paper.html](https://openaccess.thecvf.com/content/CVPR2025/html/Duggal_Eval3D_Interpretable_and_Fine-grained_Evaluation_for_3D_Generation_CVPR_2025_paper.html)
