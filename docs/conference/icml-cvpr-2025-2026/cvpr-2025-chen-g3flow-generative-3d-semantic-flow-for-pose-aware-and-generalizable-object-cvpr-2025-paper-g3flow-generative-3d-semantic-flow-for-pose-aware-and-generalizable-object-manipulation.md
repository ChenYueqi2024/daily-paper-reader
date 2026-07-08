---
title: "G3Flow: Generative 3D Semantic Flow for Pose-aware and Generalizable Object Manipulation"
title_zh: G3Flow：面向姿态感知和泛化物体操作的生成式3D语义流
authors: "Chen, Tianxing, Mu, Yao, Liang, Zhixuan, Chen, Zanxin, Peng, Shijia, Chen, Qiangyu, Xu, Mingkun, Hu, Ruizhen, Zhang, Hongyuan, Li, Xuelong, Luo, Ping"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_G3Flow_Generative_3D_Semantic_Flow_for_Pose-aware_and_Generalizable_Object_CVPR_2025_paper.pdf"
tags: ["query:dm"]
score: 7.0
evidence: 结合生成与理解的3D语义流用于物体操作
tldr: 针对机器人操作中几何精度与语义理解分离的问题，本文提出G3Flow，通过结合3D生成模型创建数字孪生、视觉基础模型提取语义特征和鲁棒位姿跟踪，构建动态物体级3D语义表示。该方法在遮挡下仍保持完整语义，无需人工标注。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
motivation: 机器人操作需融合几何与语义，现有方法难以兼顾。
method: 利用3D生成模型、视觉基础模型和位姿跟踪联合构建实时语义流。
result: 在多种操作任务上验证了语义表示的有效性和泛化性。
conclusion: 生成式3D语义流可提升机器人对物体的理解与操作能力。
---

## Abstract
Recent advances in imitation learning for 3D robotic manipulation have shown promising results with diffusion-based policies. However, achieving human-level dexterity requires seamless integration of geometric precision and semantic understanding. We present G3Flow, a novel framework that constructs real-time semantic flow, a dynamic, object-centric 3D semantic representation by leveraging foundation models. Our approach uniquely combines 3D generative models for digital twin creation, vision foundation models for semantic feature extraction, and robust pose tracking for continuous semantic flow updates. This integration enables complete semantic understanding even under occlusions while eliminating manual annotation requirements. By incorporating semantic flow into diffusion policies, we demonstrate significant improvements in both terminal-constrained manipulation and cross-object generalization. Extensive experiments across five simulation tasks show that G3Flow consistently outperforms existing approaches, achieving up to 68.3% and 50.1% average success rates on terminal-constrained manipulation and cross-object generalization tasks respectively. Our results demonstrate the effectiveness of G3Flow in enhancing real-time dynamic semantic feature understanding for robotic manipulation policies.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义
- **研究动机**：现有3D机器人操作模仿学习方法（如基于点云的扩散策略）虽然具备几何精度，但缺乏语义理解，导致在姿态感知操作（如确定鞋尖朝向、工具把手位置）和跨物体泛化（同一类别不同几何形状的物体）时表现不佳。
- **整体含义**：本文提出 G3Flow，通过融合 **3D生成模型**、**视觉基础模型** 和 **实时位姿跟踪**，构建物体级动态语义流，使得操作策略既能保持几何精确性，又能理解物体语义部分，从而实现更精准、更泛化的机器人操作。

## 2. 方法论
- **核心思想**：利用基础模型在离线阶段构建完整的物体语义场，再通过在线位姿跟踪将语义场与真实物体实时对齐，保持语义在遮挡下的完整性，并将其作为条件注入扩散策略中。
- **关键技术细节**：
  - **阶段一：初始语义流构建**
    - **物体中心探索**：使用 Grounded-SAM 检测和分割物体，通过机械臂腕部摄像头主动采集多视角 RGB-D 观测，克服单视角自遮挡问题。
    - **数字孪生生成**：基于 Rodin 等 3D 生成模型，从多视角观测重建高保真数字孪生，利用模型先验补全遮挡部分。
    - **虚拟语义流生成**：在虚拟空间中从多个视角渲染数字孪生的 RGB 图像，使用 DINOv2 提取特征，再经 PCA 降维（保留5维），结合虚拟深度信息生成初始语义点云（1024点）。
  - **阶段二：动态语义流维护**
    - **空间对齐与实时跟踪**：通过 FoundationPose 进行6D位姿跟踪，利用公式 \( P_{T_{\text{update}}} = [(M_{c2w} M_{\text{update}})(M_{c2w} M_{\text{init}})^{-1}] P_{T_{\text{init}}} \) 将初始语义流变换到当前帧，实现遮挡鲁棒的语义更新。
  - **G3Flow增强扩散策略**：
    - 多模态条件编码：语义流特征 \( f_s \)、真实点云特征 \( f_r \)、机器人关节状态 \( f_p \) 分别通过 MLP 编码。
    - 条件去噪过程：DDIM 调度器，噪声预测损失 \( L = MSE(\epsilon_k, \epsilon_\theta(\bar{\alpha}_k a_0 + \bar{\beta}_k \epsilon_k, k, f_s, f_r, f_p)) \)。

## 3. 实验设计
- **数据集/场景**：基于 RoboTwin benchmark 的5个模拟操作任务：Shoe Place、Dual Shoes Place、Tool Adjust、Bottle Adjust、Diverse Bottles Pick。每个任务包含100个专家演示用于训练。
- **Benchmark**：分别评估 **终端约束操作**（需要精确姿态控制）和 **跨物体泛化**（同一类别不同几何形状的物体）两类能力。
- **对比方法**：
  - DP（2D Diffusion Policy，图像输入）
  - 3D DP（3D Diffusion Policy，点云输入）
  - 3D DP w/ color（点云+RGB颜色）
  - 消融实验中还对比了 scene-level DINOv2 特征和 D³Fields（GenDP）方法。

## 4. 资源与算力
- 文中未明确说明训练使用的 GPU 型号、数量及训练时长。
- 推理速度测试在 **单张 NVIDIA GeForce RTX 4090** 上进行，G3Flow 的决策频率为 **34.04 Hz**（远高于对比方法的 6.89 Hz 和 9.52 Hz）。
- 训练配置：G3Flow 和 DP3 训练 3000 epoch，batch size 256；DP 训练 300 epoch，batch size 128。

## 5. 实验数量与充分性
- **实验数量**：
  - 5个任务 × 2类评估（终端约束 + 泛化）= 10组主要结果。
  - 每组使用3个随机种子，每个种子100个测试 episode，报告均值和标准差。
  - 消融实验：效率对比（表3）、语义场质量对比（表4，2个任务）、VFM 替换对比（表5，1个任务）。
  - 可视化分析（图10）展示语义流在遮挡下的稳定性。
- **充分性与公平性**：
  - 实验设计较充分，涵盖了不同任务类型、不同泛化难度。
  - 与多种基线公平对比，并报告了方差，体现统计可靠性。
  - 但 **仅在模拟环境中验证**，未涉及真实机器人实验，这是主要不足。

## 6. 主要结论与发现
- G3Flow 在 **终端约束操作** 上平均成功率 68.3%，超过最佳基线 3D DP（46.2%）约22个百分点。
- 在 **跨物体泛化** 上平均成功率 50.1%，超过最佳基线 3D DP（31.7%）约18个百分点。
- 消融实验表明：物体级语义流优于场景级特征和 D³Fields；DINOv2 作为视觉基础模型优于 CLIP 和 SAM。
- 决策频率 34.04 Hz 满足实时操作需求，效率远优于现有方法。

## 7. 优点
- **方法创新**：首次将3D生成模型、视觉基础模型和位姿跟踪有机结合，实现无需人工标注的完整语义流。
- **遮挡鲁棒性**：利用数字孪生和离线语义场，结合在线位姿跟踪，即使在机械臂遮挡下也能保持语义完整。
- **多任务泛化**：在同类不同几何形状以及跨类别工具上均表现出强泛化能力，证明了语义理解的有效性。
- **计算效率高**：在一次数字孪生和特征提取后，后续仅需轻量级位姿跟踪，推理速度快。

## 8. 不足与局限
- **缺乏真实机器人验证**：所有实验在仿真中进行，未展示在真实物理环境中的表现，可能存在 sim-to-real gap。
- **依赖初始3D生成模型**：数字孪生质量直接影响语义流准确性，对于罕见或结构复杂物体可能重建不佳。
- **适用范围有限**：当前仅处理刚性单物体操作，未涉及铰接物体、可变形物体或多物体交互。
- **手动特征降维**：PCA 降维至5维可能丢失部分语义细节，虽然提升了效率但可能影响极精细操作。
- **仅评估了固定专家演示数量**：未探讨不同演示数量下方法的数据效率。

（完）
