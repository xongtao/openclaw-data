# ProteinAE Rebuttal 对话整理

> **论文**: ProteinAE: Protein Diffusion Autoencoders for Structure Encoding  
> **会议**: ICLR 2026 Poster  
> **整理时间**: 2026-03-13

---

## 对话结构

```
审稿人 FiwP
    ↓ 提出问题
作者回复
    ↓ 回应疑问
审稿人 MnGk
    ↓ 提出问题
作者回复
...
```

---

## 💬 审稿人 FiwP ↔ 作者

### 🔴 审稿人 FiwP 的核心质疑

**Q1:** - In this work, the authors propose using a non-equivariant diffusion autoencoder called ProteinAE to encode protein structure by directly mapping backbone coordinates into a continuous latent space. And they show the performance of their model compared to recent generative frameworks along with its...

### 🟢 作者回复

**A1:** - Our perspective on the necessity of SE(3) equivariance distinguishes between two categories of tasks: - [2] Geffner, Tomas, et al. \Proteina: Scaling flow-based protein structure generative models.\ ICLR 2025. - [3] Zitnick, Larry, et al. \Spherical channels for modeling atomic interactions.\ NeurIPS 2022: 8054-8067. - [4] Ding, Yuhui, and Thomas Hofmann. \Scalable Non-Equivariant 3D Molecule Ge...

---

## 💬 审稿人 MnGk ↔ 作者

### 🔴 审稿人 MnGk 的核心质疑

**Q1:** - This paper proposes PROTEINAE, a protein diffusion autoencoder mapping protein backbone coordinates from E(3) into a continuous, compact latent space for protein modeling and generation. PROTEINAE uses a non-equivariant Diffusion Transformer and is trained with a single flow matching objective to ...

**Q2:** - [1] Geffner, Tomas, et al. \Proteina: Scaling flow-based protein structure generative models.\ arXiv preprint arXiv:2503.00710 (2025) [2] Geffner, Tomas, et al. \La-proteina: Atomistic protein generation via partially latent flow matching.\ arXiv preprint arXiv:2507.09466 (2025).

**Q3:** - Please refer to the weakness section

### 🟢 作者回复

**A1:** - These adjustments led to the improved results shown in the updated Table (see Comment 3 response). - [1] Esser, Patrick, et al. \Scaling rectified flow transformers for high-resolution image synthesis.\ Forty-first international conference on machine learning. 2024. - [2] Zheng, Boyang, et al. \Diffusion Transformers with Representation Autoencoders.\ arXiv preprint arXiv:2510.11690 (2025). - Co...

---

## 💬 审稿人 qmAJ ↔ 作者

### 🔴 审稿人 qmAJ 的核心质疑

**Q1:** - This paper proposed PROTEINAE, a protein diffusion autoencoder that learns compact, continuous representations of protein structures directly from 3D backbone coordinates in Euclidean space (E(3)).

**Q2:** - Unlike prior approaches that depend on SE(3)-equivariant models, discrete tokenization, or multiple loss functions, PROTEINAE simplifies training with a single flow-matching objective and a non-equivariant Diffusion Transformer (DiT) architecture. The model efficiently encodes protein backbones in...

**Q3:** - The authors argue that strict equivariance may not be essential for effective protein representation learning, citing recent advances such as AlphaFold3 and Proteina, which also employ non-equivariant architectures. However, the paper could benefit from a more comprehensive discussion of related w...

### 🟢 作者回复

**A1:** - [1] Fu, Cong, et al. \A latent diffusion model for protein structure generation.\ Learning on graphs conference. PMLR, 2024. - [2] Yim, Jason, et al. \SE (3) diffusion model with application to protein backbone generation.\ arXiv preprint arXiv:2302.02277 (2023). - [3] Watson, Joseph L., et al. \De novo design of protein structure and function with RFdiffusion.\ Nature 620.7976 (2023): 1089-1100...

---

## 💬 审稿人 dnyu ↔ 作者

### 🔴 审稿人 dnyu 的核心质疑

**Q1:** - This paper proposes a new generative model for protein tertiary structure generation and reconstruction. Most existing approaches rely on coordinate prediction models or diffusion models based on stochastic noise denoising, which are computationally expensive and often struggle to maintain structu...

**Q2:** - The proposed framework consists of three stages. In the first stage, the model takes the backbone atoms of each residue as input and compresses them into residue-level representations using an All-Atom Attention Encoder, which is designed to capture both spatial dependencies among residue pairs an...

**Q3:** - Experimental evaluation on protein structures from the AlphaFold Database demonstrates that the proposed method achieves smoother and more stable structure generation than conventional diffusion models, with higher reconstruction accuracy as measured by RMSD and FAPE. The generated structures also...

### 🟢 作者回复

**A1:** - Similarly, I believe the primary advantage of incorporating SE(3) equivariance lies in ligand modeling. Recent works, such as Pearl [1], have reintroduced SO(3) into the AlphaFold3 architecture, resulting in strong performance in ligand docking. However, this improvement could also be attributed to the contribution of synthetic data. Another approach involves using energy functions as potentials...

---

## 📊 Rebuttal 要点总结

### 主要争议点

| 审稿人 | 核心问题 | 作者回应策略 |
|--------|----------|--------------|
| **FiwP** | 1. SE(3) 等变性必要性<br>2. 缺少 CAMEO 基准<br>3. 下游任务验证不足 | 1. 区分两类任务（生成 vs 物理模拟）<br>2. 补充 CAMEO 实验<br>3. 增加 Bind/Cat/Con 任务 |
| **MnGk** | 1. 结构方法 vs 潜空间方法<br>2. 非物理结构风险<br>3. 缺少 Proteina/La-proteina 对比 | 1. time-shifting + 扩大通道<br>2. 等变性测试 + 物理验证<br>3. 添加 Proteina 对比 |
| **qmAJ** | 1. 缺少 LatentDiff 相关工作讨论<br>2. 非等变模型理论依据不足 | 1. 补充 LatentDiff 讨论<br>2. 详细阐述 SE(3) 分类观点 |
| **dnyu** | 1. 未来是否引入等变机制<br>2. 大分子结构适用性 | 1. 计划 ProteinAE v2<br>2. 验证几何一致性通过 |

### 作者的核心论点

1. **SE(3) 等变性不是必须的** - 区分"生成/重构/跨模态任务"和"物理理解/力场任务"
2. **近似等变性可通过数据增强学习** - 实验证明 ProteinAE 生成结构物理有效
3. **非等变架构可扩展性更好** - 参考 AlphaFold3、Proteina 等最新工作

### 补充实验

- ✅ CAMEO 基准测试
- ✅ Proteina 基线对比
- ✅ 等变性测试 (Er, Eu, E)
- ✅ 物理验证 (Ramachandran, bond lengths/angles)
- ✅ 下游任务 (Bind, Cat, Con)

---

*由 OpenClaw 自动整理*
