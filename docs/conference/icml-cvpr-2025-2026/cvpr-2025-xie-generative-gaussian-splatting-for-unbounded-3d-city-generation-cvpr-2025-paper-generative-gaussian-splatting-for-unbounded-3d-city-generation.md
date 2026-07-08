---
title: Generative Gaussian Splatting for Unbounded 3D City Generation
title_zh: 用于无边界3D城市生成的生成式高斯泼溅
authors: "Xie, Haozhe, Chen, Zhaoxi, Hong, Fangzhou, Liu, Ziwei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Xie_Generative_Gaussian_Splatting_for_Unbounded_3D_City_Generation_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 9.0
evidence: 使用高斯泼溅进行无边界3D城市生成
tldr: 针对无边界3D城市生成中存储开销大的问题，提出GaussianCity框架，采用生成式高斯泼溅技术，通过单前向传播高效合成大规模城市场景，实验表明在10km²场景中显著降低显存占用并生成高质量结果。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1807, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1767, \"height\": 878, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1790, \"height\": 1257, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1802, \"height\": 888, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1805, \"height\": 539, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1813, \"height\": 391, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 402, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 874, \"height\": 234, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-xie-generative-gaussian-splatting-for-unbounded-3d-city-generation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 875, \"height\": 234, \"label\": \"Table\"}]"
motivation: NeRF和现有3D-GS方法在无限尺度城市生成中面临计算低效和显存不足问题。
method: 提出GaussianCity框架，利用生成式高斯泼溅进行单次前馈合成。
result: 在10km²城市场景中大幅降低显存占用，生成高质量结果。
conclusion: 生成式高斯泼溅可高效扩展至无限尺度3D城市生成。
---

## Abstract
3D city generation with NeRF-based methods shows promising generation results but is computationally inefficient. Recently 3D Gaussian splatting (3D-GS) has emerged as a highly efficient alternative for object-level 3D generation. However, adapting 3D-GS from finite-scale 3D objects and humans to infinite-scale 3D cities is non-trivial. Unbounded 3D city generation entails significant storage overhead (out-of-memory issues), arising from the need to expand points to billions, often demanding hundreds of Gigabytes of VRAM for a city scene spanning 10km^2. In this paper, we propose **GaussianCity**, a generative Gaussian splatting framework dedicated to efficiently synthesizing unbounded 3D cities with a single feed-forward pass. Our key insights are two-fold: **1)** *Compact 3D Scene Representation*: We introduce BEV-Point as a highly compact intermediate representation, ensuring that the growth in VRAM usage for unbounded scenes remains constant, thus enabling unbounded city generation. **2)** *Spatial-aware Gaussian Attribute Decoder*: We present spatial-aware BEV-Point decoder to produce 3D Gaussian attributes, which leverages Point Serializer to integrate the structural and contextual characteristics of BEV points. Extensive experiments demonstrate that GaussianCity achieves state-of-the-art results in both drone-view and street-view 3D city generation. Notably, compared to CityDreamer, GaussianCity exhibits superior performance with a speedup of 60 times (10.72 FPS v.s. 0.18 FPS).

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：3D城市生成在游戏、动画、电影和VR等领域具有广泛应用前景。现有基于NeRF的方法（如InfiniCity、CityDreamer）虽然在无限尺度3D城市生成中取得了有希望的结果，但计算效率低下，推理速度慢且细节丢失。
- **背景**：3D高斯泼溅（3D-GS）作为NeRF的高效替代方案，在物体级3D生成中表现优异，但直接将其扩展到无限尺度3D城市时面临严重的内存和存储问题。随着场景规模增大（如10km²），3D高斯点数量膨胀至数十亿，导致显存占用达到数百GB，无法实际运行。
- **核心问题**：如何将3D-GS高效地应用于无限尺度3D城市生成，克服显存和存储爆炸的瓶颈。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- **紧凑场景表示（BEV-Point）**：提出一种高度紧凑的中间表示——BEV-Point，将高斯属性解耦为位置相关属性和风格相关属性。位置属性压缩到鸟瞰图（BEV）地图中，风格属性压缩到风格查找表中。只有可见的BEV点参与渲染和优化，使显存占用随场景规模扩大保持恒定。
- **空间感知高斯属性解码器**：设计BEV-Point解码器，利用Point Serializer将无序的BEV点转换为有序结构，再通过Point Transformer捕获结构性和上下文特征，最终由调制MLP生成高斯属性。

### 关键技术细节
1. **BEV-Point初始化**：从局部BEV地图（高度场H、语义图S、二值密度图D）通过拉伸像素生成BEV点坐标\(C_F\)。利用射线相交获得可见性图V，仅保留可见点\(C_A\)，大幅减少点数。
2. **BEV-Point特征生成**：包含三类特征：
   - 实例属性：实例标签I、实例大小S(l)、实例中心C(l)。
   - 点属性：绝对坐标\(C_A\)、相对坐标\(C_R\)（相对于实例中心归一化）、场景特征\(F_S\)（由场景编码器E从BEV地图提取，通过绝对坐标索引）。
   - 风格查找表T：将实例标签映射为风格隐向量\(Z_T\)，从正态分布采样。
3. **BEV-Point解码**：
   - 位置编码器P：将相对坐标和场景特征连接后编码为高维嵌入\(F_P\)。
   - Point Serializer L：将点坐标映射为整数顺序，公式为\(o = \lfloor x/g^2 + y/g + z \rfloor\)（g为网格大小），使邻近点空间接近，便于后续处理。
   - Point Transformer F：对序列化特征进行变换，得到特征\(F_T\)。
   - 调制MLP M：结合序列化特征、风格隐向量和实例标签，生成高斯属性A（仅包含RGB值）。
   - Gaussian Rasterizer R：根据相机内外参和属性渲染图像。
4. **损失函数**：混合L1损失、VGG感知损失和GAN对抗损失。

## 3. 实验设计

### 数据集
- **GoogleEarth数据集**：来自Google Earth Studio，包含纽约曼哈顿和布鲁克林的400条轨道轨迹，每条60张图像，提供相机参数、3D语义和建筑实例分割。
- **KITTI-360数据集**：大规模室外郊区数据集，约73.7km驾驶距离，包含3D边界框标注（建筑、汽车、道路等）。

### Benchmark
- 评估指标：FID、KID（图像质量）、Depth Error (DE，三维几何精度）、Camera Error (CE，多视图一致性）、Runtime（推理速度）。
- 对比方法：
  - GoogleEarth上：SGAM、PersistentNature、SceneDreamer、InfiniCity、CityDreamer。
  - KITTI-360上：StyleGAN2、GSN、GIRAFFE、UrbanGIRAFFE。

### 实验设置
- 图像分辨率：GoogleEarth上随机裁剪至448×448，KITTI-360上448×224。
- 生成帧数：GoogleEarth 15K帧，KITTI-360 5K帧。
- 深度误差评估：100帧。
- 用户研究：20名志愿者评估三类指标（感知质量、3D真实感、视图一致性），评分1-5。

## 4. 资源与算力

- **训练硬件**：8块NVIDIA Tesla V100 GPU，训练200,000次迭代，batch size为8。
- **测试硬件**：NVIDIA Tesla A100，用于推理时间测量（960×540图像，平均100次迭代）。
- **未明确说明**：具体训练时长未给出，但可推断为大规模训练（200k迭代，8卡V100）。

## 5. 实验数量与充分性

- **主要定量实验**：在GoogleEarth和KITTI-360两个数据集上，与5-6个基线方法对比，报告了FID、KID、DE、CE、Runtime等指标，结果全面（见表1）。
- **消融实验**：共4组：
  1. BEV-Point表示的有效性（不同可见性策略、密度图的影响，表2）。
  2. BEV-Point解码器组件（Point Serializer和Point Transformer的贡献，表3）。
  3. 序列化方法比较（公式(13) vs Hilbert曲线，表4）。
- **用户研究**：20名志愿者评估，结果用柱状图展示（图5），覆盖GoogleEarth和KITTI-360。
- **定性对比**：提供多组可视化结果（图3、图4），直观展示生成质量。
- **充分性评价**：实验覆盖不同场景（航拍和街景）、多种评价指标、充分的消融，且所有对比方法使用作者提供的代码重新训练保证公平（InfiniCity除外），整体充分且客观。

## 6. 主要结论与发现

- GaussianCity在GoogleEarth和KITTI-360上均达到SOTA，FID/KID最优，深度误差和相机误差最低。
- 推理速度远超NeRF方法：相比CityDreamer提速60倍（10.72 FPS vs 0.18 FPS），且显存占用恒定为1.39-1.41 GB，远低于3D-GS的显存爆炸。
- BEV-Point表示和Point Serializer是核心贡献，缺一不可。
- 用户研究中，感知质量、3D真实感和视图一致性均显著优于所有基线。

## 7. 优点

- **方法创新**：首次将3D-GS扩展到无限尺度城市生成，提出紧凑的BEV-Point表示和空间感知解码器，显存恒定且存储效率高。
- **效率极高**：单前向传播生成，推理速度比NeRF方法快两个数量级，显存占用极低。
- **生成质量高**：在航拍和街景场景均输出高真实感、结构合理的图像，减少了伪影和失真。
- **实验全面**：覆盖两个高质量数据集，与众多基线公平对比，消融实验揭示关键设计的作用。
- **用户研究支持**：主观评价证实了方法的优越性。

## 8. 不足与局限

- **几何假设限制**：BEV-Point初始化假设建筑符合曼哈顿假设（垂直拉伸），无法表示空心结构（如拱门、隧道）。
- **高斯属性预测不全**：当前仅预测RGB值，未充分利用3D-GS的全部表达能力（如缩放、旋转、不透明度），因为同时预测过多属性会训练不稳定。
- **依赖BEV地图**：需要预先提供语义图、高度场等BEV地图，其获取可能依赖外部预测模型，限制了完全零样本能力。
- **实验覆盖**：仅在两个城市数据集上验证，未在更多样化的城市或乡村场景测试；用户研究参与者仅20人，样本量较小。
- **应用限制**：由于需要BEV地图和实例信息，当前方法更适用于有先验知识的城市生成，直接泛化到未知场景可能受限。

（完）
