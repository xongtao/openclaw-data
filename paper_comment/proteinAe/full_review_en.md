# ProteinAE: Complete Review Process

**Paper**: ProteinAE: Protein Diffusion Autoencoders for Structure Encoding  
**Conference**: ICLR 2026 Conference  
**Submission Number**: 11944  
**Final Decision**: Accept (Poster)

---

## Table of Contents

1. [Paper Decision](#1-paper-decision)
2. [Meta Review](#2-meta-review)
3. [Summary of Revisions](#3-summary-of-revisions)
4. [Reviewer Dialogues](#4-reviewer-dialogues)
   - [Reviewer FiwP](#reviewer-fiwp)
   - [Reviewer MnGk](#reviewer-mngk)
   - [Reviewer qmAJ](#reviewer-qmaj)
   - [Reviewer dnyu](#reviewer-dnyu)

---

## 1. Paper Decision

**Decision:** Accept (Poster)  
**By:** Program Chairs  
**Date:** 26 Jan 2026, 16:42 (modified: 06 Feb 2026, 13:20)  
**Visibility:** Everyone

---

## 2. Meta Review

**Title:** Meta Review of Submission11944 by Area Chair x5kH  
**By:** Area Chair x5kH  
**Date:** 07 Jan 2026, 03:52 (modified: 09 Feb 2026, 14:41)

### Summary
The paper proposes a diffusion model for protein structure encoding. The reviewers split on their original judgement and the authors have provided detailed rebuttals.

### Reviewer Concerns
Reviewers were concerned about model equivariance, and experimental data and comparison, and it seems most of them have been addressed.

### Reviewer Scores
The reviewer scores split between positive and negative.

---

## 3. Summary of Revisions

**Title:** Summary of Revisions and Response to Reviewers  
**By:** Authors  
**Date:** 30 Nov 2025, 00:58 (modified: 01 Dec 2025, 15:24)

We would like to thank you and the reviewers for the time and effort dedicated to reviewing our work. The constructive feedback has helped us significantly improve the quality and completeness of our manuscript.

We have actively engaged with all reviewers and provided a comprehensive revision. Below is a summary of the key updates addressing the reviewers' main concerns:

### 1. Expanded Benchmarks & Baselines (Addressing Reviewers FiwP & MnGk)

- New Baselines: Added comparisons with Proteina (as requested by Reviewer MnGk) to better position our work within the recent landscape of non-equivariant models.
- CAMEO Benchmark: Conducted additional evaluations on the CAMEO dataset (requested by Reviewer FiwP), demonstrating that our model's reconstruction quality remains robust beyond CASP14/15.

### 2. Enhanced Generative Performance & Designability (Addressing Reviewers MnGk & FiwP)

- Improved Generation Quality: Demonstrated improved generation quality by implementing a time-shifting technique and scaling up the model channel dimensions.

### 3. Equivariance, Validity & Related Work (Addressing Reviewers FiwP, MnGk & qmAJ)

- SE(3) & Physical Consistency: Expanded the discussion on the trade-offs of SE(3) equivariance. Clarified how our Flow Matching objective and network design ensure physical plausibility and geometric robustness without the computational overhead of strict equivariance.
- Related Work: Incorporated a detailed discussion of LatentDiff (requested by Reviewer qmAJ) to distinguish our contribution.

### 4. Downstream Utility (Addressing Reviewer FiwP)

- Extended evaluation to include Bind, Cat and Con, showing competitive performance.

### 5. Perspective of ProteinAE v2 (Addressing Reviewer dnyu)

- Future Roadmap & Multi-Modal Support: Outlined the development of ProteinAE v2, including support for larger complexes and multi-modal conditioning.

---

## 4. Reviewer Dialogues

### Reviewer FiwP

**Summary:** This paper presents ProteinAE, a non-equivariant diffusion autoencoder for protein structure encoding. The work challenges the conventional wisdom that SE(3) equivariance is essential for protein modeling.

**Strengths:**
- Novel application of non-equivariant modeling
- Fast structural encoder
- Challenges the equivariance paradigm

**Weaknesses:**
- Needs more careful explanation of SE(3) trade-offs
- Missing CAMEO benchmark
- Limited downstream task evaluation

### Dialogue

**Question 1:** SE(3) representations are essential in protein structure modeling. The point needs to be explained more carefully.

> **Response:** Our perspective distinguishes between two categories: Generation/Reconstruction tasks (where strict equivariance is not mandatory) and Physical Understanding/Force Fields (where SE(3) is critical). ProteinAE learns approximate SE(3) equivariance through data augmentation.

**Question 2:** It would be good to see the performance on CAMEO as well.

> **Response:** We have conducted additional evaluations on the CAMEO dataset, demonstrating robust reconstruction quality beyond CASP14/15.

**Question 3:** Evaluating performance on downstream tasks like GO-term prediction could better illustrate practical impact.

> **Response:** We have extended evaluation to include Bind, Cat and Con tasks, showing competitive performance.

---

### Reviewer MnGk

**Summary:** ProteinAE uses a non-equivariant Diffusion Transformer with a single flow matching objective. It achieves better reconstruction quality and high-quality structure generation.

**Strengths:**
- Novel non-equivariant approach
- Simplified training with single objective
- Good reconstruction quality

**Weaknesses:**
- Structure-based methods still better
- Risk of non-physical structures without equivariance
- Missing La-proteina and Proteina baselines

### Dialogue

**Question 1:** Structure-based method is still better than the latent-based model. Could authors elaborate more?

> **Response:** We improved generation quality by implementing time-shifting technique and scaling up model channel dimensions. These adjustments led to improved results in the updated Table.

**Question 2:** Would not considering equivariance lead to generating non-physical structures?

> **Response:** Tested on proteins of varying lengths (100-500 residues). ProteinAE shows high geometric validity: Ramachandran 0.00% violation, bond lengths 1.24% violation, bond angles 1.10% violation.

**Question 3:** The comparison missed important baselines La-proteina and Proteina.

> **Response:** We have added comparisons with Proteina to better position our work within the recent landscape of non-equivariant models.

---

### Reviewer qmAJ

**Summary:** ProteinAE simplifies training with a single flow-matching objective and non-equivariant DiT architecture. It achieves SOTA reconstruction accuracy on CASP14/15.

**Strengths:**
- Simplified model design and training
- State-of-the-art reconstruction accuracy
- Computational efficiency advantages

**Weaknesses:**
- Lacks sufficient discussion of prior work
- Could benefit from deeper theoretical justification for non-equivariant choice

### Dialogue

**Question 1:** This paper lacks sufficient discussion of prior work. For example, LatentDiff is compared in Table 2 but not discussed in related-work section.

> **Response:** We apologize for this oversight. We have added detailed discussion: LatentDiff employs an SE(3)-equivariant graph autoencoder, achieving sampling speeds orders of magnitude faster than frame-based approaches.

**Question 2:** The paper would benefit from a deeper theoretical justification for choosing a non-equivariant model.

> **Response:** Recent SOTA works—AlphaFold 3, Proteina, SCN, RADM, and ADiT—have increasingly adopted scalable non-equivariant architectures. This represents a shifting trend: non-equivariant models avoid complex components like spherical harmonics, allowing more efficient scaling.

---

### Reviewer dnyu

**Summary:** ProteinAE combines Flow Matching with Transformer-based network for continuous structure generation. It adopts a non-equivariant architecture on E(3) space, eliminating costly rotation/translation handling while maintaining geometric robustness.

**Strengths:**
- Novel non-equivariant framework
- Efficient structure generation
- Maintains geometric robustness

**Weaknesses:**
- Future direction for larger complexes

### Dialogue

**Question 1:** Do the authors have plans for incorporating additional constraints or equivariant mechanisms for larger and more complex protein structures?

> **Response:** We outlined the development of ProteinAE v2 for larger complexes. The primary advantage of SE(3) equivariance lies in ligand modeling. Recent works like Pearl have reintroduced SO(3) into AlphaFold3. Our validation confirms ProteinAE achieves high geometric validity and learns approximate equivariance via data augmentation.

---

