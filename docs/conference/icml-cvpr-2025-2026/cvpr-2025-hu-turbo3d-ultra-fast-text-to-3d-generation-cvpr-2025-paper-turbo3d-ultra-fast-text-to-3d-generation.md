---
title: "Turbo3D: Ultra-fast Text-to-3D Generation"
title_zh: Turbo3D：超快速文本到3D生成
authors: "Hu, Hanzhe, Yin, Tianwei, Luan, Fujun, Hu, Yiwei, Tan, Hao, Xu, Zexiang, Bi, Sai, Tulsiani, Shubham, Zhang, Kai"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Hu_Turbo3D_Ultra-fast_Text-to-3D_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 超快速文本到3D生成
tldr: 针对文本到3D生成速度慢的问题，本文提出Turbo3D，通过双教师蒸馏实现4步4视图扩散生成器，并结合潜在空间高斯重建器，在1秒内生成高质量高斯泼溅资产。该方法在速度和质量上均超越基线。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1785, \"height\": 1301, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1804, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 396, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 318, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1377, \"height\": 1302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1620, \"height\": 847, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 305, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-hu-turbo3d-ultra-fast-text-to-3d-generation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 242, \"label\": \"Table\"}]"
motivation: 现有文本到3D生成方法效率低，难以实时应用。
method: 采用双教师蒸馏的4步多视图扩散生成器和潜在空间高斯重建器。
result: 在不到1秒内生成高质量3D资产，速度与精度领先。
conclusion: 蒸馏与潜在空间操作可极大加速3D生成，推动实时应用。
---

## Abstract
We present Turbo3D, an ultra-fast text-to-3D system capable of generating high-quality Gaussian splatting assets in under one second. Turbo3D employs a rapid 4-step, 4-view diffusion generator, and an efficient feed-forward Gaussian reconstructor, both operating in latent space. The 4-step, 4-view generator is a student model distilled through a novel Dual-Teacher approach, which encourages the student to learn view consistency from a multi-view teacher and photo-realism from a single-view teacher. By shifting the Gaussian reconstructor's inputs from pixel space to latent space, we eliminate the extra image decoding time and halve the transformer sequence length for maximum efficiency. Our method demonstrates superior 3D generation results compared to previous baselines, while operating in a fraction of their runtime.

---

## 论文详细总结（自动生成）

# Turbo3D: Ultra-fast Text-to-3D Generation 论文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：现有的文本到3D生成方法主要分为两类：优化驱动的方法（如DreamFusion）需要数分钟甚至数小时生成一个3D资产，效率极低；前馈生成方法（如Instant3D）虽然更快，但受限于多视图扩散模型的迭代去噪过程，推理速度仍不够快。此外，现有方法在生成质量、文本对齐和跨域泛化方面存在不足。为此，论文旨在实现“超快速”文本到3D生成（<1秒），同时保持高质量。
- **核心挑战**：如何将多视图扩散模型蒸馏成极少数步（4步）的生成器，同时避免因蒸馏造成的模式坍塌（即生成结果过于卡通化、缺乏真实感），以及如何优化3D重建环节的推理效率。
- **整体含义**：Turbo3D通过双教师蒸馏（Dual-Teacher Distillation）和潜在空间高斯重建器（Latent GS-LRM），首次在1秒内（0.35秒）完成从文本到高质量3D高斯泼溅（3DGS）资产的生成，在速度上比现有方法快一个数量级以上，且质量达到或超越慢速多步教师模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 2.1 整体框架（图1）
- 两阶段流水线：① 快速4步、4视图的潜在空间扩散生成器（few-step MV diffusion generator）；② 单步前馈高斯重建器（Latent GS-LRM）。
- 所有操作均在潜在空间（latent space）中进行，避免VAE解码的额外时间，并将Transformer序列长度减半。

### 2.2 双教师蒸馏（Dual-Teacher Distillation）
- **核心思想**：为解决学生模型仅从多视图教师蒸馏时发生的“复合模式坍塌”（compounding mode collapse）问题，引入第二个教师——单视图（SV）教师，该教师是经过大量高质量美学图像训练的2D去噪扩散模型。
- **公式（7）**：总蒸馏损失 = 多视图DMD损失 + ρ × K分之一 × 单视图DMD损失，其中ρ=1，K=4（视图数）。
  - 多视图DMD损失：基于Distribution Matching Distillation（DMD），优化学生输出分布与多视图数据分布之间的反向KL散度。
  - 单视图DMD损失：对每个视图单独计算与单视图教师的反向KL散度。
- **训练过程**：学生模型（4步多视图扩散）通过Plücker嵌入增强3D感知，教师模型权重固定；同时训练一个动态的“假得分函数”来模拟学生输出的分布。

### 2.3 潜在空间高斯重建器（Latent GS-LRM）
- 将先前像素空间的GS-LRM [62] 改为直接输入多视图潜在特征（latents），输出3D高斯泼溅参数。
- 训练时使用像素空间的新视角渲染损失（L2 + 感知损失）进行监督。
- 优势：跳过VAE解码（节省约0.1秒），并因潜在空间空间尺寸更小（如32×32 vs 128×128）而减少Transformer序列长度，进一步加速。

## 3. 实验设计：数据集、基准、对比方法

- **数据集**：Objaverse数据集（约730K个物体，渲染16/32视图，使用Cap3D文本标注）。训练分为三个阶段：
  - 多步多视图扩散模型：Objaverse渲染的16个等距方位角（固定仰角20°）。
  - 蒸馏阶段：使用同样的渲染数据。
  - 重建模型：随机32视图（距离1.5~2.8）渲染。
- **评估基准**：使用DreamFusion的400个文本提示，每个提示生成一个3D对象。评价指标：
  - CLIP Score（语义对齐）
  - VQA Score（视觉问答得分，基于NaturalBench）
  - 推理时间（统一256分辨率下A100 GPU）。
- **对比方法**：
  - 文本到3D：Instant3D [17]、LGM [47]
  - 图像到3D（需先用文本到图像模型Flux生成图像）：TripoSR [49]、SV3D [51]
  - 同时也与自己的多步教师模型（MV Teacher）对比。

## 4. 资源与算力

- **训练硬件**：32块80G A100 GPU。
- **训练时长与迭代次数**：
  - 多步多视图扩散模型：30k迭代，全局batch size 128，学习率3e-5。
  - 蒸馏阶段：10k迭代，全局batch size 128，学习率5e-6。
  - 潜在重建模型：80k迭代，全局batch size 256，学习率4e-4。
- **推理**：单张A100 GPU，0.35秒（Turbo3D完整流水线）。

## 5. 实验数量与充分性

论文主要进行了以下实验：
1. **定量对比**（表1）：与四种基线方法（TripoSR、SV3D、Instant3D、LGM）比较CLIP、VQA和推理时间。
2. **定性对比**（图4）：展示6组复杂文本提示下的生成结果对比。
3. **用户研究**（图5）：80个提示，56位用户，1120个成对比较，比较Turbo3D与LGM、Instant3D、MV Teacher。
4. **消融实验**：
   - 双教师 vs 单教师蒸馏（表2、图6）：证明SV教师对缓解模式坍塌的必要性。
   - 潜在GS-LRM vs 像素GS-LRM（表3、图3）：证明潜在空间重构在几乎相同质量下提速22%。
5. **与慢速MV教师对比**（表2、图6）：学生模型质量几乎无损失（CLIP: 27.61 vs 28.04；VQA: 0.76 vs 0.77）。
- **充分性评价**：实验设计较为全面，覆盖了主要性能指标、消融关键组件、用户偏好，且与多种类型基线（文本-3D、图像-3D）对比。但消融实验仅涉及两个核心组件，未对蒸馏步数、教师权重ρ、视图数K进行深入探索。用户研究样本量（80提示）虽然合理，但未提供统计显著性检验。

## 6. 论文的主要结论与发现

- **Turbo3D能在0.35秒内生成高质量3DGS资产**，比最先进的快速方法Instant3D（15.02秒）快约43倍，同时CLIP和VQA分数显著更高（27.61 vs 26.23；0.76 vs 0.65）。
- **双教师蒸馏有效避免了模式坍塌**：仅用MV教师蒸馏会导致卡通化效果（CLIP下降1.44分），加入SV教师后几乎恢复教师质量（仅下降0.43分）。
- **潜在空间GS-LRM在无质量损失下实现~22%速度提升**，且保留了与像素空间版本相当的渲染质量。
- 用户研究中，Turbo3D以74.9%的胜率战胜Instant3D，以89.8%的胜率战胜LGM，与慢速MV教师持平（50.6%）。

## 7. 优点：方法或实验设计上的亮点

- **创新性**：首次将扩散蒸馏（DMD）成功应用于多视图生成，并针对3D场景提出双教师蒸馏框架，解决了复合模式坍塌这一关键问题。
- **效率优先设计**：整个流水线（生成+重建）均在潜在空间运作，避免冗余编解码，并大幅缩短Transformer序列长度，实现亚秒级推理。
- **实验设计严谨**：同时进行了定量、定性、用户研究和消融实验，且与多种类型基线对比，验证了方法的优越性。
- **开源友好**：论文提供了项目网址，并声明将发布模型。

## 8. 不足与局限

- **仅基于Objaverse训练**：Objaverse数据多为合成物体，可能限制对真实世界复杂场景（如室内环境、非中心化物体）的泛化能力。
- **文本提示长度和复杂度有限**：评估仅使用了DreamFusion的400个提示，未测试超长或极抽象提示。
- **消融实验不够全面**：未探索蒸馏步数（如1步 vs 4步）、教师权重ρ、视图数K等超参数的影响，也未对重建模型的不同架构做对比。
- **潜在偏差风险**：单视图教师训练自高质量美学图像，可能引入特定风格偏好（如过度平滑或高对比度），导致某些类型提示生成结果偏离真实分布。
- **应用限制**：仅生成3DGS表示，后续若需要网格（mesh）仍需额外处理；此外，3DGS的极端视角（如背面）可能出现伪影。
- **未与最新优化方法对比**：未与ProlificDreamer等基于SDS的优化方法比较（虽然侧重不同），但可作为速度对比参考。
- 论文未提供可复现的代码或模型权重，仅承诺开源。

（完）
