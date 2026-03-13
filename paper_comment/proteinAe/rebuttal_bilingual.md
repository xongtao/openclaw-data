# ProteinAE Rebuttal Summary (Bilingual) / 评审回复总结 (中英对照)

**Paper**: ProteinAE: Protein Diffusion Autoencoders for Structure Encoding  
**Conference**: ICLR 2026  
**Status**: Accepted (Poster) / 状态：接收 (Poster)

---

### Reviewer FiwP / 审稿人 FiwP

**Question 1 / 问题 1：**

> In the introduction, authors mention that other models use SE(3) representations and are therefore slow. However, SE(3) representations are also essential in protein structure modeling specifically in generative protein design, so this point needs to be explained more carefully.

> *作者在引言中提到其他模型使用 SE(3) 表示因此较慢。但 SE(3) 表示在蛋白质结构建模（特别是生成式设计）中也是必需的，这一点需要更仔细地解释。*

**Question 2 / 问题 2：**

> Authors include CASP14 and CASP15 in their benchmark. It would be good to see the performance on CAMEO as well for the same period as ESM3.

> *作者在基准测试中包含了 CASP14 和 CASP15。希望也能看到与 ESM3 相同时期在 CAMEO 上的表现。*

**Question 3 / 问题 3：**

> Evaluating its performance on other downstream structure-based prediction tasks, such as GO-term prediction, could better illustrate the practical impact of the approach.

> *评估该方法在其他基于结构的预测任务（如 GO 术语预测）上的表现，可以更好地说明该方法的实际影响。*

**Response 1 / 回复 1：**

> We thank the reviewer for raising this important point regarding the trade-offs of SE(3) equivariance. Our perspective distinguishes between two categories of tasks: Generation/Reconstruction/Cross-modal Tasks (where strict equivariance is not mandatory) and Physical Understanding/Force Fields (where SE(3) equivariance is critical). We demonstrate that ProteinAE learns approximate SE(3) equivariance through data augmentation.

> *感谢审稿人提出关于 SE(3) 等变性权衡的重要问题。我们的观点区分了两类任务：生成/重构/跨模态任务（其中严格等变性不是必需的）和物理理解/力场任务（其中 SE(3) 等变性至关重要）。我们证明 ProteinAE 通过数据增强学习近似 SE(3) 等变性。*

**Response 2 / 回复 2：**

> We thank the reviewer for this valuable suggestion. We have conducted additional evaluations on the CAMEO dataset, demonstrating that our model's reconstruction quality remains robust beyond CASP14/15.

> *感谢审稿人的宝贵建议。我们已在 CAMEO 数据集上进行了额外评估，证明我们的模型在 CASP14/15 之外的重建质量依然稳健。*

**Response 3 / 回复 3：**

> We appreciate the reviewer for pointing this out. We have extended our evaluation to include Bind, Cat and Con tasks, showing competitive performance.

> *感谢审稿人的指出。我们已扩展评估范围，包括 Bind、Cat 和 Con 任务，展示了具有竞争力的性能。*

---

### Reviewer MnGk / 审稿人 MnGk

**Question 1 / 问题 1：**

> Structure-based method is still better than the latent-based model. Could authors elaborate more on that?

> *基于结构的方法仍然优于基于潜空间的方法。作者能否详细说明这一点？*

**Question 2 / 问题 2：**

> PROTEINAE doesn't consider equivariance to simplify the design but would that lead to generating non-physical structures?

> *PROTEINAE 为了简化设计不考虑等变性，但这会导致生成非物理结构吗？*

**Question 3 / 问题 3：**

> The comparison missed some important baselines, La-proteina and Proteina.

> *对比中缺少了一些重要的基线，如 La-proteina 和 Proteina。*

**Response 1 / 回复 1：**

> We thank the reviewer for this critical observation. We have improved generation quality by implementing a time-shifting technique and scaling up the model channel dimensions. These adjustments led to improved results shown in the updated Table.

> *感谢审稿人的关键观察。我们通过实现时间偏移技术和扩大模型通道维度来改进生成质量。这些调整带来了更新表格中显示的改进结果。*

**Response 2 / 回复 2：**

> We tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). ProteinAE shows high geometric validity with Ramachandran 0.00% violation, bond lengths 1.24% violation, and bond angles 1.10% violation.

> *我们在 100-500 残基长度的蛋白质上测试了 ProteinAE 与 ESM3 VQ-VAE 的对比。ProteinAE 显示出高几何有效性：Ramachandran 违规率 0.00%，键长违规率 1.24%，键角违规率 1.10%。*

**Response 3 / 回复 3：**

> We have added comparisons with Proteina to better position our work within the recent landscape of non-equivariant models.

> *我们已添加与 Proteina 的对比，以更好地将我们的工作定位在最近的非等变模型领域中。*

---

### Reviewer qmAJ / 审稿人 qmAJ

**Question 1 / 问题 1：**

> This paper lacks sufficient discussion of prior work on 3D protein backbone structure autoencoder design. For example, the model LatentDiff is compared in Table 2, but it is not discussed in the related-work section.

> *本文缺乏对 3D 蛋白质骨架结构自编码器先前工作的充分讨论。例如，LatentDiff 模型在表 2 中有对比，但在相关工作部分没有讨论。*

**Question 2 / 问题 2：**

> The authors argue that strict equivariance may not be essential. However, the paper would benefit from a deeper theoretical justification for choosing a non-equivariant model.

> *作者认为严格等变性可能不是必需的。然而，论文需要更深入的理论依据来解释选择非等变模型的原因。*

**Response 1 / 回复 1：**

> We apologize for this oversight and thank the reviewer for bringing LatentDiff to our attention. We have added detailed discussion: LatentDiff employs an SE(3)-equivariant graph autoencoder to map protein backbones into latent representations, achieving sampling speeds orders of magnitude faster than frame-based approaches.

> *我们对这一疏忽表示歉意，并感谢审稿人指出 LatentDiff。我们已添加详细讨论：LatentDiff 采用 SE(3) 等变图自编码器将蛋白质骨架映射到潜在表示中，实现比基于框架的方法快几个数量级的采样速度。*

**Response 2 / 回复 2：**

> We appreciate the opportunity to clarify. Recent SOTA works—AlphaFold 3, Proteina, SCN, RADM, and ADiT—have increasingly adopted scalable non-equivariant architectures. This represents a shifting trend: non-equivariant models possess simpler structures, avoiding complex components like spherical harmonics, allowing them to scale up parameters and training data more efficiently.

> *我们感谢有这个澄清的机会。最近的 SOTA 工作——AlphaFold 3、Proteina、SCN、RADM 和 ADiT——越来越多地采用可扩展的非等变架构。这代表了一种转变趋势：非等变模型具有更简单的结构，避免了球谐函数等复杂组件，使其能够更有效地扩展参数和训练数据。*

---

### Reviewer dnyu / 审稿人 dnyu

**Question 1 / 问题 1：**

> Do the authors have any ideas or future plans for incorporating additional constraints or introducing some form of equivariant mechanism to extend the applicability to larger and more complex protein structures?

> *作者是否有计划引入额外约束或某种等变机制，以扩展模型对更大更复杂蛋白质结构的适用性？*

**Response 1 / 回复 1：**

> We outlined the development of ProteinAE v2 for larger complexes. The primary advantage of SE(3) equivariance lies in ligand modeling. Recent works like Pearl have reintroduced SO(3) into AlphaFold3 for ligand docking. Our validation confirms ProteinAE achieves high geometric validity and learns approximate equivariance effectively via data augmentation.

> *我们概述了用于更大复合物的 ProteinAE v2 的开发计划。SE(3) 等变性的主要优势在于配体建模。最近如 Pearl 等工作已将 SO(3) 重新引入 AlphaFold3 用于配体对接。我们的验证确认 ProteinAE 实现了高几何有效性，并通过数据增强有效学习近似等变性。*

---

