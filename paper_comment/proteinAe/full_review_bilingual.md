# ProteinAE: Complete Review Process / 完整评审流程 (中英对照)

**Paper / 论文**: ProteinAE: Protein Diffusion Autoencoders for Structure Encoding  
**Conference / 会议**: ICLR 2026  
**Final Decision / 最终决定**: Accept (Poster) / 接收 (Poster)

---

## 1. Paper Decision / 论文决定

**Decision / 决定:** Accept (Poster) / 接收 (Poster)  
**By / 决定人:** Program Chairs / 程序主席  
**Date / 日期:** 26 Jan 2026 / 2026年1月26日

> 中文解释：论文被接收为海报展示（Poster），这是ICLR会议的一种接收形式，通常表示论文质量良好但可能不需要进行口头报告。

---

## 2. Meta Review / 元评审

**Title / 标题:** Meta Review of Submission11944 by Area Chair x5kH / 投稿11944的元评审 - 领域主席 x5kH  
**By / 评审人:** Area Chair x5kH / 领域主席 x5kH  
**Date / 日期:** 07 Jan 2026 / 2026年1月7日

### Summary / 总结
The paper proposes a diffusion model for protein structure encoding. The reviewers split on their original judgement and the authors have provided detailed rebuttals.

> 中文解释：本文提出了一个用于蛋白质结构编码的扩散模型。审稿人对原始判断存在分歧，作者提供了详细的反驳意见。

### Reviewer Concerns / 审稿人关注点
Reviewers were concerned about model equivariance, and experimental data and comparison, and it seems most of them have been addressed.

> 中文解释：审稿人们对模型的等变性（equivariance，指模型在旋转/平移变换下的不变性）、实验数据和对比实验表示担忧，但这些问题似乎大部分已得到解决。

### Reviewer Scores / 审稿人评分
The reviewer scores split between positive and negative.

> 中文解释：审稿人评分在正面（支持接收）和负面（反对接收）之间分歧，没有形成一致意见。

---

## 3. Summary of Revisions / 修订总结

**Title / 标题:** Summary of Revisions and Response to Reviewers / 修订总结及对审稿人的回复  
**By / 作者:** Authors / 论文作者  
**Date / 日期:** 30 Nov 2025 / 2025年11月30日

We would like to thank you and the reviewers for the time and effort dedicated to reviewing our work.

> 中文解释：我们要感谢领域主席和审稿人投入时间和精力评审我们的工作。

### 1. Expanded Benchmarks & Baselines / 扩展基准与基线
New Baselines: Added comparisons with Proteina to better position our work within the recent landscape of non-equivariant models.

> 中文解释：新基线：添加了与 Proteina 的对比，Proteina 是一种最近的非等变蛋白质生成模型，用于更好地定位我们工作在研究领域中的位置。

CAMEO Benchmark: Conducted additional evaluations on the CAMEO dataset, demonstrating that our model's reconstruction quality remains robust beyond CASP14/15.

> 中文解释：CAMEO 基准：CAMEO 是一个持续的蛋白质结构预测评估项目，我们在此数据集上的额外评估证明模型在 CASP14/15 之外依然表现稳健。

### 2. Enhanced Generative Performance / 增强生成性能
Improved Generation Quality: Demonstrated improved generation quality by implementing a time-shifting technique and scaling up the model channel dimensions.

> 中文解释：改进生成质量：通过实现时间偏移（time-shifting）技术和扩大模型通道维度，展示了改进的生成质量。时间偏移是扩散模型中的一种技术，用于改善采样质量。

### 3. Equivariance, Validity & Related Work / 等变性、有效性与相关工作
SE(3) & Physical Consistency: Expanded the discussion on the trade-offs of SE(3) equivariance. Clarified how our Flow Matching objective ensures physical plausibility without strict equivariance.

> 中文解释：SE(3) 与物理一致性：SE(3) 是三维空间中的特殊欧几里得群（旋转+平移）。扩展了对 SE(3) 等变性权衡的讨论，澄清了我们的流匹配（Flow Matching）目标函数如何在不严格强制等变性的情况下确保物理合理性。

Related Work: Incorporated a detailed discussion of LatentDiff to distinguish our contribution.

> 中文解释：相关工作：LatentDiff 是另一种蛋白质结构生成的潜在扩散模型，我们增加了对其的详细讨论以区分我们的贡献。

### 4. Downstream Utility / 下游实用性
Extended evaluation to include Bind, Cat and Con tasks, showing competitive performance.

> 中文解释：将评估扩展到包括 Bind（结合）、Cat（催化）和 Con（构象）任务，这些是蛋白质功能预测的典型任务，展示了具有竞争力的性能。

### 5. Perspective of ProteinAE v2 / ProteinAE v2 展望
Future Roadmap: Outlined the development of ProteinAE v2, including support for larger complexes and multi-modal conditioning.

> 中文解释：未来路线图：概述了 ProteinAE v2 的开发计划，包括对更大蛋白质复合物的支持和多模态条件控制（结合序列、功能等信息）。

---

## 4. Reviewer Dialogues / 审稿人对话

### Reviewer FiwP / 审稿人 FiwP

**Summary / 总结:** This paper presents ProteinAE, a non-equivariant diffusion autoencoder. The work challenges the conventional wisdom that SE(3) equivariance is essential.

> 本文提出了 ProteinAE，一个非等变扩散自编码器。该工作挑战了传统的 SE(3) 等变性对蛋白质建模至关重要的观念。

**Question / 问题:** SE(3) representations are also essential in protein structure modeling specifically in generative protein design, so this point needs to be explained more carefully.

> 中文解释：SE(3) 表示在蛋白质结构建模（特别是生成式设计）中也是必需的，这一点需要更仔细地解释。

**Response / 回复:** Our perspective distinguishes between two categories: Generation/Reconstruction tasks (where strict equivariance is not mandatory) and Physical Understanding/Force Fields (where SE(3) is critical). ProteinAE learns approximate SE(3) equivariance through data augmentation.

> 中文解释：我们的观点区分了两类任务：生成/重构任务（其中严格等变性不是必需的）和物理理解/力场任务（其中 SE(3) 至关重要）。ProteinAE 通过数据增强学习近似 SE(3) 等变性。

**Question / 问题:** It would be good to see the performance on CAMEO as well.

> 中文解释：希望也能看到在 CAMEO（持续评估项目）上的表现。

**Response / 回复:** We have conducted additional evaluations on the CAMEO dataset, demonstrating robust reconstruction quality beyond CASP14/15.

> 中文解释：我们在 CAMEO 数据集上进行了额外评估，证明在 CASP14/15 之外的重建质量依然稳健。

**Question / 问题:** Evaluating performance on downstream tasks like GO-term prediction could better illustrate practical impact.

> 中文解释：评估在下游任务（如 GO 术语预测）上的表现可以更好地说明实际影响。GO（Gene Ontology）是基因功能的标准化描述。

**Response / 回复:** We have extended evaluation to include Bind, Cat and Con tasks, showing competitive performance.

> 中文解释：我们已扩展评估范围，包括 Bind（结合）、Cat（催化）和 Con（构象）任务，展示了具有竞争力的性能。

---

### Reviewer MnGk / 审稿人 MnGk

**Summary / 总结:** ProteinAE uses a non-equivariant Diffusion Transformer. It achieves better reconstruction quality and high-quality structure generation.

> ProteinAE 使用非等变扩散变换器。它实现了更好的重建质量和高质量的生成。

**Question / 问题:** Structure-based method is still better than the latent-based model. Could authors elaborate more?

> 中文解释：基于结构的方法仍然优于基于潜空间的方法。作者能否详细说明？

**Response / 回复:** We improved generation quality by implementing time-shifting technique and scaling up model channel dimensions.

> 中文解释：我们通过实现时间偏移技术和扩大模型通道维度来改进生成质量。

**Question / 问题:** Would not considering equivariance lead to generating non-physical structures?

> 中文解释：不考虑等变性会导致生成非物理结构吗？

**Response / 回复:** Tested on proteins of varying lengths. ProteinAE shows high geometric validity: Ramachandran 0.00% violation, bond lengths 1.24% violation, bond angles 1.10% violation.

> 中文解释：在不同长度的蛋白质上测试。ProteinAE 显示出高几何有效性：Ramachandran 图违规率 0.00%（衡量蛋白质骨架构象合理性的标准），键长违规率 1.24%，键角违规率 1.10%。

**Question / 问题:** The comparison missed important baselines La-proteina and Proteina.

> 中文解释：对比缺少了一些重要的基线 La-proteina 和 Proteina（两者都是最近的非等变蛋白质生成模型）。

**Response / 回复:** We have added comparisons with Proteina to better position our work within the recent landscape of non-equivariant models.

> 中文解释：我们已添加与 Proteina 的对比，以更好地将我们的工作定位在最近的非等变模型领域中。

---

### Reviewer qmAJ / 审稿人 qmAJ

**Summary / 总结:** ProteinAE simplifies training with a single flow-matching objective. It achieves SOTA reconstruction accuracy on CASP14/15.

> ProteinAE 使用单一流匹配目标函数简化了训练。在 CASP14/15 上实现了 SOTA（最先进）重建精度。CASP 是蛋白质结构预测的关键评估实验。

**Question / 问题:** This paper lacks sufficient discussion of prior work. For example, LatentDiff is compared in Table 2 but not discussed in related-work section.

> 中文解释：本文缺乏对先前工作的充分讨论。例如，LatentDiff 在表2中有对比，但在相关工作部分没有讨论。

**Response / 回复:** We apologize for this oversight. We have added detailed discussion: LatentDiff employs an SE(3)-equivariant graph autoencoder, achieving sampling speeds orders of magnitude faster than frame-based approaches.

> 中文解释：我们对这一疏忽表示歉意。我们已添加详细讨论：LatentDiff 采用 SE(3) 等变图自编码器，实现比基于框架的方法快几个数量级的采样速度。

**Question / 问题:** The paper would benefit from a deeper theoretical justification for choosing a non-equivariant model.

> 中文解释：论文需要更深入的理论依据来解释选择非等变模型的原因。

**Response / 回复:** Recent SOTA works—AlphaFold 3, Proteina, SCN, RADM, and ADiT—have increasingly adopted scalable non-equivariant architectures. This represents a shifting trend: non-equivariant models avoid complex components like spherical harmonics, allowing more efficient scaling.

> 中文解释：最近的 SOTA 工作——AlphaFold 3、Proteina、SCN、RADM 和 ADiT——越来越多地采用可扩展的非等变架构。这代表了一种转变趋势：非等变模型避免了球谐函数（spherical harmonics，传统等变模型使用的复杂数学组件）等复杂组件，使其能够更有效地扩展。

---

### Reviewer dnyu / 审稿人 dnyu

**Summary / 总结:** ProteinAE combines Flow Matching with Transformer for continuous structure generation. It adopts a non-equivariant architecture on E(3) space.

> ProteinAE 将流匹配与 Transformer 相结合，用于连续结构生成。它在 E(3) 空间（三维欧几里得空间）上采用非等变架构。

**Question / 问题:** Do the authors have plans for incorporating additional constraints or equivariant mechanisms for larger and more complex protein structures?

> 中文解释：作者是否有计划引入额外约束或等变机制，以扩展模型对更大更复杂蛋白质结构的适用性？

**Response / 回复:** We outlined the development of ProteinAE v2 for larger complexes. The primary advantage of SE(3) equivariance lies in ligand modeling. Recent works like Pearl have reintroduced SO(3) into AlphaFold3. Our validation confirms ProteinAE achieves high geometric validity and learns approximate equivariance via data augmentation.

> 中文解释：我们概述了用于更大复合物的 ProteinAE v2 的开发计划。SE(3) 等变性的主要优势在于配体建模（ligand modeling，小分子与蛋白质相互作用）。最近如 Pearl 等工作已将 SO(3)（旋转群）重新引入 AlphaFold3。我们的验证确认 ProteinAE 实现了高几何有效性，并通过数据增强学习近似等变性。

---

