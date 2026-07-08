---
title: "3D-RFT: Reinforcement Fine-Tuning for Video-based 3D Scene Understanding"
title_zh: 3D-RFT：基于视频的3D场景理解的强化学习微调
authors: "Xiongkun Linghu, Jiangyong Huang, Baoxiong Jia, Siyuan Huang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/68c4430379f506213a9f95bc64217bc834c7ee2f.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 基于视频的3D场景理解结合强化学习微调
tldr: 针对3D场景理解中强化学习应用缺失的问题，提出3D-RFT框架，通过监督微调激活3D感知后，利用GRPO和可验证3D奖励（如IoU、F1）进行强化微调，在视频输入的3D场景理解任务上显著提升性能。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: LLM的强化学习能力尚未被有效应用于3D场景理解。
method: 两阶段：监督微调激活3D感知，再用GRPO结合可验证奖励强化微调。
result: 在视频3D场景理解任务上显著优于现有方法。
conclusion: 可验证奖励的强化学习可提升3D场景理解能力。
---

## Abstract
Reinforcement Learning with Verifiable Rewards (RLVR) has emerged as a key paradigm for unlocking complex reasoning in Large Language Models (LLMs), yet its potential in 3D scene understanding remains untapped. To bridge this gap, we present Reinforcement Fine-Tuning for Video-based 3D Scene Understanding (3D-RFT), the first framework to extend RLVR to 3D perception and reasoning. Our pipeline operates in two stages: activating 3D-aware Multi-modal Large Language Models (MLLMs) via Supervised Fine-Tuning (SFT), followed by reinforcement fine-tuning using Group Relative Policy Optimization (GRPO) with strictly verifiable reward functions. We design task-specific rewards—such as 3D IoU and F1-score—to provide deterministic signals for spatial alignment. Extensive experiments demonstrate that 3D-RFT achieves state-of-the-art performance on video-based 3D scene understanding benchmarks, significantly outperforming VG LLM-8B on detection and grounding tasks. Moreover, our model surpasses larger mainstream models on VSI-Bench, demonstrating the efficiency of verifiable reinforcement learning. We conclude by offering valuable insights into optimal training strategies .

---

## 论文详细总结（自动生成）

# 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：尽管基于可验证奖励的强化学习（RLVR）在大语言模型（LLM）的复杂推理能力解锁中已展现关键作用，但在3D场景理解领域，这一范式的潜力尚未被探索。现有3D场景理解方法缺乏利用强化学习进行精细对齐和推理优化的途径。
- **核心问题**：如何将RLVR有效扩展到视频输入的3D场景理解任务（包括3D感知与推理），从而提升模型的空间对齐精度和推理能力。
- **整体含义**：本文提出3D-RFT，首个将RLVR框架引入3D场景理解的尝试，旨在填补强化学习在3D领域应用的空白，为多模态大模型（MLLM）在3D空间理解中提供新的训练范式。

# 2. 论文提出的方法论

- **核心思想**：采用两阶段训练流水线：先通过监督微调（SFT）激活模型的3D感知能力，再使用强化学习（GRPO）结合严格可验证的奖励函数进行强化微调，从而提升3D场景理解和推理性能。
- **关键技术细节**：
  - **第一阶段：监督微调（SFT）**：在3D视频数据上对多模态大语言模型（MLLM）进行微调，使其具备基础的3D感知能力，例如识别物体、定位、空间关系等。
  - **第二阶段：强化微调（Reinforcement Fine-Tuning）**：使用**组相对策略优化（GRPO, Group Relative Policy Optimization）**作为强化学习算法，并设计任务特定的**可验证奖励函数**，包括：
    - 3D IoU（Intersection over Union）：衡量预测3D包围框与真值的空间重叠程度。
    - F1-score：用于检测和定位任务中正负样本的平衡评估。
  - 这些奖励提供**确定性信号**，严格评估空间对齐质量，避免主观或难以量化的反馈。
- **算法流程（文字说明）**：
  1. 在视频3D场景数据集上，通过SFT预热MLLM，使其输出初步合理的3D感知结果。
  2. 在强化微调阶段，模型对同一输入生成多个候选输出（组），由GRPO算法计算组内相对优势，结合可验证奖励对模型策略进行优化。
  3. 奖励函数直接基于地面真值标签计算（如IoU、F1），确保训练信号客观、可重复。

# 3. 实验设计

- **使用数据集/场景**：视频输入的3D场景理解基准测试，包括**VSI-Bench**（可能是Video-based Scene Interpretation Benchmark）以及检测和定位任务的标准数据集（具体名称未在摘要中列出，但提到检测和接地任务）。
- **Benchmark**：论文在视频3D场景理解基准上进行评估，并与现有方法对比。
- **对比方法**：
  - **VG LLM-8B**：作为基线模型，3D-RFT在检测和接地任务上显著超越它。
  - **更大的主流模型**：在VSI-Bench上，3D-RFT以较小的参数量（基于8B规模）超越了更大规模的主流模型，验证了强化学习的效率。

# 4. 资源与算力

- **未明确说明**：论文摘要及元数据中未提及具体使用的GPU型号、数量、训练时长或总计算成本。仅在动机和方法中强调“效率”，但无定量数据。

# 5. 实验数量与充分性

- **实验数量**：摘要中仅提到“extensive experiments”，具体实验组数未列出。但根据结论，涉及了在不同基准（如VSI-Bench、检测/接地任务）上的对比，以及可能的消融研究（从“offering valuable insights into optimal training strategies”推断）。
- **充分性与公平性**：
  - **充分性**：实验覆盖了视频3D场景理解的核心任务（检测、接地）和综合基准（VSI-Bench），并对比了同类及更大模型，为性能提升提供了有力证据。
  - **客观性**：使用严格可验证奖励（IoU、F1），避免了主观评分偏差，实验结果可复现。但缺少更细粒度的消融实验细节（如不同奖励组合、SFT vs. 强化微调单独贡献）的公开描述。
  - **公平性**：对比了同规模（VG LLM-8B）和更大规模的模型，表明方法在效率上的优势，但未说明对比方法是否采用类似的训练数据或强化学习策略。

# 6. 论文的主要结论与发现

- 3D-RFT在视频3D场景理解基准上取得了**最先进（state-of-the-art）**性能，尤其在检测和接地任务上显著优于VG LLM-8B。
- 在VSI-Bench上，3D-RFT超越了更大的主流模型，证明**可验证强化学习能够高效提升3D场景理解能力**。
- 提出了首个将RLVR成功应用于3D感知与推理的框架，并验证了两阶段训练策略（SFT后强化微调）的有效性。
- 可验证奖励（如IoU、F1）为空间对齐提供了确定性信号，是性能提升的关键。

# 7. 优点

- **创新性**：首次将RLVR范式引入3D场景理解领域，填补了强化学习在3D感知中的空白。
- **奖励设计**：采用严格可验证的3D任务指标（IoU、F1）作为奖励，保证反馈的客观性和可复现性，避免了主观或学习型奖励的偏差。
- **训练效率**：仅使用8B规模模型即超越更大规模主流模型，表明强化微调能够高效利用参数，无需巨大算力。
- **方法论清晰**：两阶段流水线（SFT激活→GRPO强化）逻辑明确，易于复现和扩展。

# 8. 不足与局限

- **实验覆盖有限**：摘要中仅提及视频输入的3D场景理解，未说明是否适用于静态3D数据或其他模态（如图像、点云），泛化能力未知。
- **算力与资源未公开**：没有量化计算成本，难以评估方法的实际落地门槛。
- **缺乏更广泛的消融研究**：未详细分析不同奖励权重、GRPO超参数、SFT阶段数据量等对性能的影响，可能遗漏最优配置。
- **应用限制**：奖励函数依赖于地面真值标签（IoU/F1），在无真值标注的开放场景下无法直接使用；且只针对检测和定位任务，对其他3D任务（如语义分割、运动预测）未涉及。
- **潜在偏差风险**：若训练数据中存在标注偏差或长尾分布，GRPO可能放大这些偏差，但论文未讨论。
- **对比方法不够全面**：仅与VG LLM-8B和部分主流模型对比，未与专门针对3D场景理解的非强化学习方法（如PointNet系列、3D Transformers）进行比较。

（完）
