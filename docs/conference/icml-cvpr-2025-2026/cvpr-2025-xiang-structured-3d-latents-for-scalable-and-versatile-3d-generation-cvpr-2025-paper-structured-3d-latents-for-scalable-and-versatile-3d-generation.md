---
title: Structured 3D Latents for Scalable and Versatile 3D Generation
title_zh: 用于可扩展通用3D生成的结构化3D潜在表示
authors: "Xiang, Jianfeng, Lv, Zelong, Xu, Sicheng, Deng, Yu, Wang, Ruicheng, Zhang, Bowen, Chen, Dong, Tong, Xin, Yang, Jiaolong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Xiang_Structured_3D_Latents_for_Scalable_and_Versatile_3D_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 基于结构潜在表示的可扩展通用3D生成
tldr: 针对3D生成中表示缺乏通用性的问题，提出结构化潜在表示SLAT，可解码为辐射场、高斯泼溅和网格等多种格式，结合整流扩散变压器在50万物体数据集上训练20亿参数模型，实现高质量多格式3D生成。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有3D表示形式单一，难以兼顾多种输出格式。
method: 设计SLAT表示，结合稀疏3D网格和多视角视觉特征，用整流变压器生成。
result: 在500K物体上训练，支持高质量多格式输出。
conclusion: 结构化潜在表示可统一不同3D输出格式。
---

## Abstract
We introduce a novel 3D generation method for versatile and high-quality 3D asset creation.The cornerstone is a unified Structured LATent (SLAT) representation which allows decoding to different output formats, such as Radiance Fields, 3D Gaussians, and meshes. This is achieved by integrating a sparsely-populated 3D grid with dense multiview visual features extracted from a powerful vision foundation model, comprehensively capturing both structural (geometry) and textural (appearance) information while maintaining flexibility during decoding.We employ rectified flow transformers tailored for SLAT as our 3D generation models and train models with up to 2 billion parameters on a large 3D asset dataset of 500K diverse objects. Our model generates high-quality results with text or image conditions, significantly surpassing existing methods, including recent ones at similar scales. We showcase flexible output format selection and local 3D editing capabilities which were not offered by previous models. Code, model, and data will be released.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有3D生成方法受限于特定的3D表示（如网格、辐射场、3D高斯泼溅），不同表示之间难以统一，导致生成模型缺乏通用性和灵活性。与2D图像生成领域已建立统一潜在空间不同，3D领域缺少一种能解码为多种高质量输出格式的标准化潜在表示。
- **研究动机**：旨在开发一种统一且通用的潜在空间，能够同时编码几何和外观信息，并支持解码为多种下游3D表示（辐射场、3D高斯泼溅、网格），从而提升3D生成的质量、可扩展性和编辑能力。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：设计一种结构化的潜在表示（SLAT），将稀疏3D网格与稠密的多视图视觉特征相结合，在激活体素上定义局部潜在向量，从而同时捕获粗粒度结构和细粒度外观细节。基于SLAT，采用两阶段生成流程（先产生稀疏结构，再生成局部潜在向量），并使用整流流变压器（Rectified Flow Transformers）作为生成模型。
- **关键技术细节**：
  1. **SLAT表示**：对于3D资产，定义一组局部潜在向量 \( \{(\boldsymbol{z}_i, \boldsymbol{p}_i)\} \)，其中 \(\boldsymbol{p}_i\) 是激活体素的位置索引（稀疏3D网格），\(\boldsymbol{z}_i\) 是附着在对应体素上的潜在特征。默认网格分辨率 \(N=64\)，平均激活体素数 \(L \approx 20K\)。
  2. **编码与解码**：编码时，从多视图渲染图像中提取DINOv2特征，通过投影与平均聚合到每个激活体素，得到体素化特征 \( \boldsymbol{f} \)。然后使用稀疏VAE（基于变压器架构，包含3D移位窗口注意力）将 \(\boldsymbol{f}\) 编码为SLAT潜在变量 \(\boldsymbol{z}\)，解码时通过不同解码器（\(\mathcal{D}_{\text{GS}}\)、\(\mathcal{D}_{\text{RF}}\)、\(\mathcal{D}_{\text{M}}\)）分别输出3D高斯、辐射场或网格。训练时采用高斯解码器端到端训练编码器/解码器，其他解码器单独训练。
  3. **生成模型**：采用整流流（Rectified Flow）模型，通过条件流匹配（CFM）目标 \(\mathcal{L}_{\text{CFM}}(\theta) = \mathbb{E}_{t,\boldsymbol{x}_0,\boldsymbol{\epsilon}} \| \boldsymbol{v}_\theta(\boldsymbol{x}, t) - (\boldsymbol{\epsilon} - \boldsymbol{x}_0) \|_2^2\) 训练。两阶段生成：第一阶段用变压器 \( \mathcal{G}_S \) 生成稀疏结构（先通过3D卷积VAE压缩为低分辨率特征网格）；第二阶段用稀疏变压器 \( \mathcal{G}_L \) 生成局部潜在向量，包含下采样（稀疏卷积）、变压器模块和上采样模块，采用跳过连接。条件（文本/图像）通过交叉注意力注入。
  4. **编辑能力**：支持细节变化（保持结构，重生成潜在）和区域特定编辑（基于Repaint策略，在指定包围盒内修改体素和潜变量，保持其他区域不变）。

### 3. 实验设计：使用了哪些数据集 / 场景，其 benchmark 是什么，对比了哪些方法

- **训练数据集**：从4个公开数据集收集约50万个高质量3D资产：Objaverse (XL)、ABO、3D-FUTURE、HSSD。每个资产渲染150张图像，使用GPT-4o生成标题。
- **评估基准**：主要使用Toys4k数据集（未包含在训练集或对比方法的训练集中）进行定量评估。另外使用GPT-4生成文本、DALL-E 3生成图像进行视觉比较和用户研究。
- **对比方法**：
  - **重建对比**：CLAY、3DTopia-XL、LN3Diff，在指标上（PSNR、LPIPS、CD、F-score、法向PSNR等）超越所有基线。
  - **生成对比**：2D辅助方法（InstantMesh、LGM）和3D生成方法（GaussianCube、Shap-E、3DTopia-XL、LN3Diff）。定性比较和定量指标（CLIP分数、FD、KD等多种特征空间）均显著领先。
  - **用户研究**：100+参与者，对68个文本提示和67个图像提示生成结果进行偏好选择，本文方法获得压倒性偏好（文本：67.1%；图像：94.5%）。

### 4. 资源与算力

- **训练算力**：XL模型（20亿参数）使用64块A100 GPU（40GB显存），训练400K步，批大小256。其他模型（Basic 342M、Large 1.1B）也使用了相同集群。优化器为AdamW，学习率1e-4。

### 5. 实验数量与充分性

- **实验数量**：论文进行了多组实验：
  1. **重建实验**（表1）：在Toys4k上比较不同潜在表示的重建保真度（包括外观和几何指标）。
  2. **生成实验**（表2）：文本到3D和图像到3D的定量比较（多种特征空间的FD、KD和CLIP分数）。
  3. **用户研究**（图6）：约68+67个提示，100+参与者，结果清晰。
  4. **消融实验**（表3-5）：分别针对SLAT大小（分辨率/通道）、生成范式（整流流 vs. 扩散）、模型规模（B/L/XL）进行消融，验证设计选择。
- **充分性与公平性**：实验覆盖了重建、生成、用户偏好、多个消融维度，使用了多个公开数据集和标准指标，对比方法覆盖了主流类别。用户研究使用未经筛选的生成结果，避免挑选偏差。定量指标多样（CLIP、FD、KD、Inception/DINOv2/PointNet++特征），全面评估质量和对齐度。实验设计较为充分、客观。

### 6. 论文的主要结论与发现

- SLAT表示能够统一编码几何和外观，并支持解码为多种高质量3D表示（3D高斯、辐射场、网格），在重建保真度上大幅超越现有潜在表示。
- 基于整流流变压器的两阶段生成模型在50万物体上训练20亿参数，生成的3D资产在视觉质量和提示对齐上显著优于现有方法，包括2D辅助和3D原生方法。
- 该方法支持灵活的无调优3D编辑（细节变化和区域编辑），这是之前模型不具备的能力。
- 模型大小增加持续提升生成性能（B→L→XL），整流流优于扩散模型。

### 7. 优点：方法或实验设计上的亮点

- **表示通用性**：SLAT是首个支持解码为多种主流3D表示的潜在空间，具有很强的可扩展性。
- **高效编码**：利用预训练DINOv2特征避免专门3D编码器，无需昂贵的预拟合过程。
- **高质量生成**：在50万物体上训练大型模型，生成结果细节丰富、形状精确，且支持透明/半透明物体。
- **实验全面**：重建、生成、用户研究、消融实验多维度验证，对比方法覆盖全面，使用多种指标，统计显著性明显。
- **实际应用**：展示了区域级3D编辑能力（添加、移除、替换），且无需额外训练，具有实用价值。

### 8. 不足与局限

- **依赖多视图渲染**：编码3D资产时需要从密集多视图渲染中提取特征，对于未渲染的3D数据或动态场景可能不直接适用。
- **训练数据规模**：虽然50万物体较大，但相比2D生成模型的数据量仍有限，且数据集可能偏向某些类别（如家具、物体），在极端多样场景下泛化性未充分验证。
- **未明确局限**：论文在结论部分未详细讨论局限性。方法中网格分辨率固定为64³，可能对极精细结构有信息损失；两阶段生成流程可能累积误差；编辑策略（Repaint）依赖于边界框指定，自动化程度有限。
- **计算资源需求高**：训练20亿参数模型需要64×A100 GPU，对一般研究团队门槛较高。
- **公平性**：对比方法中未包含近期其他大规模3D生成模型（如CLAY的生成模型未公开），可能遗漏部分强基线。

（完）
