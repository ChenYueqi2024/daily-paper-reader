---
title: "WonderWorld: Interactive 3D Scene Generation from a Single Image"
title_zh: WonderWorld：从单张图片交互式生成3D场景
authors: "Yu, Hong-Xing, Duan, Haoyi, Herrmann, Charles, Freeman, William T., Wu, Jiajun"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yu_WonderWorld_Interactive_3D_Scene_Generation_from_a_Single_Image_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 8.0
evidence: 单张图片交互式3D场景生成
tldr: 针对现有3D场景生成速度慢、交互性差的问题，本文提出WonderWorld，从单张图片快速生成交互式3D场景。通过引导深度扩散实现几何一致性，并利用几何初始化大幅减少优化时间。用户可实时指定场景内容和布局，生成连贯的多场景环境。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有3D场景生成方法需要多视图逐步生成和耗时优化，交互延迟高。
method: 提出引导深度扩散和几何初始化策略，无需多视图即可快速生成连贯场景。
result: 单图输入下实现低延迟交互式3D场景生成，支持场景连接。
conclusion: 几何先验可加速场景生成并保持一致性，适用于交互式应用。
---

## Abstract
We present WonderWorld, a novel framework for interactive 3D scene generation that enables users to interactively specify scene contents and layout and see the created scenes in low latency. The major challenge lies in achieving fast generation of 3D scenes. Existing scene generation approaches fall short of speed as they often require (1) progressively generating many views and depth maps, and (2) time-consuming optimization of the scene representations. Our approach does not need multiple views, and it leverages a geometry-based initialization that significantly reduces optimization time. Another challenge is generating coherent geometry that allows all scenes to be connected. We introduce the guided depth diffusion that allows partial conditioning of depth estimation. WonderWorld generates connected and diverse 3D scenes in less than 10 seconds on a single A6000 GPU, enabling real-time user interaction and exploration. Our interactive demo, full code, data, and software can be found at https://kovenyu.com/WonderWorld/

---

## 论文详细总结（自动生成）

# WonderWorld：从单张图片交互式生成3D场景（论文总结）

## 1. 论文的核心问题与整体含义（研究动机和背景）

**研究动机**：现有3D场景生成方法（如WonderJourney、LucidDreamer、Text2Room等）均为离线模式：用户提供一张起始图片或文本提示后，系统需花费数十分钟到数小时才能返回一个固定的3D场景或视频。这种模式无法满足游戏开发、VR/AR、创意设计等场景中用户对交互式、低延迟、可迭代构建虚拟世界的需求。

**核心问题**：如何实现**交互式3D场景生成**——用户能够实时指定场景内容和布局（通过移动相机和输入文本提示），并在低延迟（秒级）内看到新生成的场景，且多个生成场景能够无缝连接成连贯的虚拟世界。

**整体含义**：本文提出第一个交互式3D场景生成框架WonderWorld，以单张图片为起点，结合用户在线控制，在10秒内生成一个场景，支持实时渲染和探索，开辟了交互式3D内容创作的新范式。

## 2. 论文提出的方法论：核心思想、关键技术细节

### 核心思想
- **加速生成**：摆脱传统方法需要渐进式生成多视图和长时间优化场景表示的瓶颈。通过**基于几何的初始化**大幅减少优化时间，并采用**单视图层生成**替代多视图合并。
- **几何一致性**：引入**引导深度扩散**（Guided Depth Diffusion），在深度估计过程中利用已有可见几何作为部分条件，减少场景连接处的几何畸变和接缝。

### 关键技术细节

#### 2.1 Fast LAyered Gaussian Surfels (FLAGS)
- **表示形式**：每个场景由三个**辐射场层**组成：前景层（L_fg）、背景层（L_bg）、天空层（L_sky）。每层是一组**高斯曲面元**（surfels），每个surfel参数化为：3D位置p、方向四元数q、x/y轴尺度s、不透明度o、与视角无关的RGB颜色c。
- **与3DGS关系**：FLAGS可视为3DGS的变体，将高斯核的z轴压缩至极小值（厚度≈0），并移除视角相关颜色，从而利用3DGS的可微渲染流水线。
- **单视图层生成**：
  - 利用LLM（GPT系列）根据用户提示生成结构化场景描述（前景/背景/风格）。
  - 文本引导的扩散模型（Stable Diffusion Inpaint）生成场景图像。
  - 通过深度边缘和分割掩码提取前景层；对背景层进行文本引导的补全；天空层独立生成。
- **几何初始化**：
  - **像素对齐**：每个surfel对应一个有效像素，颜色初始化为像素RGB，位置通过相机内参和深度反投影得到。
  - **法线初始化**：利用估计的像素法线构建surfel旋转矩阵。
  - **尺度初始化**：根据Nyquist采样定理，设置surfel尺度与采样间隔匹配，避免渲染混叠和过度重叠。
  - **不透明度初始化**：设为0.1以提供足够梯度进行微调。
- **优化**：从后往前逐层优化（天空→背景→前景），仅优化不透明度、方向和尺度，不优化颜色和位置，100次Adam迭代，无稠密化。每层优化<1秒。

#### 2.2 引导深度扩散
- **问题**：新生成场景的估计深度与已有可见几何之间存在强烈不一致，导致几何畸变。
- **方法**：在预训练潜在深度扩散模型（Marigold Depth）的推理过程中，注入部分可见深度作为引导。具体地，在每步去噪时，修改去噪器的预测噪声为：
  \[
  \hat{\epsilon}_t = \text{UNet}(d_t, I_{\text{scene}}, t) - s_t \nabla_{d_t} \| D_{t-1} \odot M_{\text{guide}} - D_{\text{guide}} \odot M_{\text{guide}} \|^2
  \]
  其中 \(D_{\text{guide}}\)、\(M_{\text{guide}}\) 为已有几何的可见深度图和掩码。该梯度项迫使生成的深度与已有几何在重叠区域一致，无需额外训练。

#### 2.3 整体流程（外循环）
1. 输入初始图像，生成第一个3D场景（FLAGS）。
2. 用户移动相机到新视角，输入文本提示。
3. 根据当前视角渲染已有场景作为参考。
4. 文本引导的扩散模型生成新场景图像（outpainting）。
5. 引导深度扩散生成与已有几何一致的深度图。
6. 单视图层生成和FLAGS优化，生成新场景。
7. 连接新场景到已有场景，返回步骤2。

## 3. 实验设计

### 数据与场景
- 使用**公开真实图像**和**合成图像**作为测试示例，包括城市、校园、自然、幻想等类型。也使用了WonderJourney和LucidDreamer论文中的示例。
- 共计4个测试示例，每个生成7个场景，共28个评估场景。

### 对比方法
- **WonderJourney**（点云表示）
- **LucidDreamer**（3DGS表示）
- **Text2Room**（网格表示）
- 使用各方法的**官方代码**进行公平比较。

### 评估指标
- **生成速度**：单场景生成时间（秒）。
- **人类主观评价**：204个鸟瞰图渲染的2AFC（两选一强制选择）偏好测试。
- **新视角质量**：
  - CLIP Score（CS）：场景文本提示与渲染图像的语义对齐。
  - CLIP Consistency（CC）：新视角与中心视角的图像CLIP嵌入余弦相似度。
  - CLIP-IQA+（CIQA）：图像质量评估。
  - Q-Align：对齐度评分。
  - CLIP Aesthetic Score（CA）：美学评分。
- **消融实验**：评估几何初始化、多层设计、深度引导三个组件的贡献。

## 4. 资源与算力

文中明确提到：
- 单场景生成在**一块NVIDIA A6000 GPU**上耗时**<10秒**（平均9.5秒）。
- 对比方法均在同一GPU上运行，WonderJourney约749.5秒，LucidDreamer约798.1秒，Text2Room约766.9秒。
- 未提及训练总时长或使用的GPU数量（方法依赖预训练模型，无需大规模重新训练）。
- 交互体验需要单GPU同时进行渲染和生成。

## 5. 实验数量与充分性

- **场景数量**：4个测试示例 × 7个场景 = 28个生成场景，用于定量比较。人类2AFC实验收集了204个样本。
- **消融实验**：3项（w/o几何初始化、w/o多层、w/o深度引导），每个消融变体同样在28个场景上评估了所有指标。
- **定性展示**：多种相机路径（全景、漫步）和多种风格（Minecraft、绘画、乐高）的视频结果。
- **充分性评价**：
  - 实验设计合理，对比了代表性方法（涵盖不同表示类型）。
  - 指标覆盖语义、一致性、质量、美学和人类偏好，较为全面。
  - 消融实验验证了每个核心组件的必要性。
  - 但场景数量相对较少（4个基础示例），且均为用户可控的“一次性”生成，没有大规模用户交互测试或多样性覆盖（如室内场景未重点考虑）。总体而言，对于交互式3D生成的首次探索，实验是充分的，但数据集规模可进一步扩大。

## 6. 论文的主要结论与发现

1. **交互式3D场景生成首次实现**：WonderWorld允许用户实时指定内容和布局，在<10秒内生成一个场景，并在单GPU上实现实时渲染。
2. **FLAGS表示有效加速**：通过几何初始化将每个场景的优化时间降至亚秒级，避免了多视图合成和时间消耗优化。
3. **引导深度扩散减少畸变**：利用部分可见深度作为条件，在无需训练的情况下显著改善场景连接处的几何一致性。
4. **优于现有方法**：在生成速度、新视角质量、人类偏好上大幅领先WonderJourney、LucidDreamer、Text2Room。CLIP Score达29.47（高于第二的27.34），人类偏好率超过98%。
5. **消融验证**：几何初始化、多层设计、深度引导三个组件均不可或缺，去除后各项指标下降，并出现渲染假体和接缝。

## 7. 优点

- **方法创新**：
  - 首次提出交互式3D场景生成问题，并给出完整框架。
  - FLAGS表示融合了分层深度图像和3DGS的优点，且设计了基于几何的初始化，极大加速优化。
  - 引导深度扩散是一种训练自由的深度对齐技术，巧妙利用扩散模型的潜力。
- **工程实践**：
  - 端到端流水线，从单张图片到可探索的3D世界仅需10秒/场景。
  - 代码、软件、交互Demo全部开源，便于复现和应用。
- **实验严谨**：
  - 使用官方代码对比，人类主观评价与多种自动指标结合。
  - 消融实验设计清晰，覆盖关键组件。

## 8. 不足与局限

- **几何限制**：生成的场景仅有**正面朝向的表面**（frontal-facing surfaces），缺乏物体背面或复杂内部结构。当视角移动过大时，会出现“空洞”或漂浮物（如树木）。
- **细节建模困难**：对精细物体（树木、复杂建筑）的建模不够准确，视图合成范围局限于相机附近区域。
- **依赖预训练模型**：生成质量受限于扩散模型（Stable Diffusion）和深度估计模型（Marigold）的能力，可能在罕见场景或极端视角下退化。
- **交互性仍有延迟**：虽然单场景<10秒，但对于连续快速移动和频繁生成的需求，可能仍不够流畅。未来可通过加速扩散推理进一步改善。
- **评估范围有限**：测试示例仅4个，且均为户外场景。未系统评估室内场景或极端光照/天气条件。
- **未引入3D物体生成模块**：作者提及未来可与GRM等3D对象生成模型结合，以补全物体背面。
- **无用户研究量化交互体验**：虽然有2AFC，但缺乏对交互流畅性、易用性、用户满意度的系统性评估。

（完）
