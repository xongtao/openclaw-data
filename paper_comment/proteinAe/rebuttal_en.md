# ProteinAE Rebuttal Summary (English)

**Paper**: ProteinAE: Protein Diffusion Autoencoders for Structure Encoding  
**Conference**: ICLR 2026  
**Status**: Accepted (Poster)

---

## Overview

This paper received reviews from 4 reviewers (FiwP, MnGk, qmAJ, dnyu). The authors provided detailed responses addressing all concerns.

---

### Reviewer FiwP

**Question 1:**
> In the introduction, authors mention that other models use SE(3) representations and are therefore slow. However, SE(3) representations are also essential in protein structure modeling specifically in generative protein design, so this point needs to be explained more carefully.

**Question 2:**
> Authors include CASP14 and CASP15 in their benchmark. It would be good to see the performance on CAMEO as well for the same period as ESM3.

**Question 3:**
> Evaluating its performance on other downstream structure-based prediction tasks, such as GO-term prediction, could better illustrate the practical impact of the approach.

**Response 1:**
> We thank the reviewer for raising this important point regarding the trade-offs of SE(3) equivariance. Our perspective distinguishes between two categories of tasks: Generation/Reconstruction/Cross-modal Tasks (where strict equivariance is not mandatory) and Physical Understanding/Force Fields (where SE(3) equivariance is critical). We demonstrate that ProteinAE learns approximate SE(3) equivariance through data augmentation.

**Response 2:**
> We thank the reviewer for this valuable suggestion. We have conducted additional evaluations on the CAMEO dataset, demonstrating that our model's reconstruction quality remains robust beyond CASP14/15.

**Response 3:**
> We appreciate the reviewer for pointing this out. We have extended our evaluation to include Bind, Cat and Con tasks, showing competitive performance.

---

### Reviewer MnGk

**Question 1:**
> Structure-based method is still better than the latent-based model. Could authors elaborate more on that?

**Question 2:**
> PROTEINAE doesn't consider equivariance to simplify the design but would that lead to generating non-physical structures?

**Question 3:**
> The comparison missed some important baselines, La-proteina and Proteina.

**Response 1:**
> We thank the reviewer for this critical observation. We have improved generation quality by implementing a time-shifting technique and scaling up the model channel dimensions. These adjustments led to improved results shown in the updated Table.

**Response 2:**
> We tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). ProteinAE shows high geometric validity with Ramachandran 0.00% violation, bond lengths 1.24% violation, and bond angles 1.10% violation.

**Response 3:**
> We have added comparisons with Proteina to better position our work within the recent landscape of non-equivariant models.

---

### Reviewer qmAJ

**Question 1:**
> This paper lacks sufficient discussion of prior work on 3D protein backbone structure autoencoder design. For example, the model LatentDiff is compared in Table 2, but it is not discussed in the related-work section.

**Question 2:**
> The authors argue that strict equivariance may not be essential. However, the paper would benefit from a deeper theoretical justification for choosing a non-equivariant model.

**Response 1:**
> We apologize for this oversight and thank the reviewer for bringing LatentDiff to our attention. We have added detailed discussion: LatentDiff employs an SE(3)-equivariant graph autoencoder to map protein backbones into latent representations, achieving sampling speeds orders of magnitude faster than frame-based approaches.

**Response 2:**
> We appreciate the opportunity to clarify. Recent SOTA works—AlphaFold 3, Proteina, SCN, RADM, and ADiT—have increasingly adopted scalable non-equivariant architectures. This represents a shifting trend: non-equivariant models possess simpler structures, avoiding complex components like spherical harmonics, allowing them to scale up parameters and training data more efficiently.

---

### Reviewer dnyu

**Question 1:**
> Do the authors have any ideas or future plans for incorporating additional constraints or introducing some form of equivariant mechanism to extend the applicability to larger and more complex protein structures?

**Response 1:**
> We outlined the development of ProteinAE v2 for larger complexes. The primary advantage of SE(3) equivariance lies in ligand modeling. Recent works like Pearl have reintroduced SO(3) into AlphaFold3 for ligand docking. Our validation confirms ProteinAE achieves high geometric validity and learns approximate equivariance effectively via data augmentation.

---

