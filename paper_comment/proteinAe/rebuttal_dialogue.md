# ProteinAE Rebuttal 对话整理

## 概述
本文共有 **4 位审稿人** (FiwP, MnGk, qmAJ, dnyu)，作者针对每位审稿人的意见进行了回复。

---

## 审稿人 FiwP ↔ 作者

### 📋 审稿人 FiwP 的主要意见

> In this work, the authors propose using a non-equivariant diffusion autoencoder called ProteinAE to encode protein structure by directly mapping backbone coordinates into a continuous latent space. And they show the performance of their model compared to recent generative frameworks along with its performance as a structure embedder for a downstream prediction task. Overall, the field has largely treated equivariance as gospel—driven by the desire to model structure from first principles and inspired by the success of AlphaFold2. However, AlphaFold3 recently shifted this paradigm. This work presents an interesting application of non-equivariant modeling for generative purposes, while also offering a fast structural encoder, though it still requires further validation and benchmarking to fully establish its advantages.

### ✍️ 作者回复

"Comment 1: In the introduction, authors mention that other models use SE(3) representations and are therefore slow. However, SE(3) representations are also essential in protein structure modeling specifically in generative protein design, so this point needs to be explained more carefully..."

"Our perspective on the necessity of SE(3) equivariance distinguishes between two categories of tasks:"

"[2] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" ICLR 2025."

"[3] Zitnick, Larry, et al. \"Spherical channels for modeling atomic interactions.\" NeurIPS 2022: 8054-8067."

"[4] Ding, Yuhui, and Thomas Hofmann. \"Scalable Non-Equivariant 3D Molecule Generation via Rotational Alignment.\" ICML 2025."

"[8] Joshi, Chaitanya K., et al. \"All-atom diffusion transformers: Unified generative modelling of molecules and materials.\" arXiv preprint arXiv:2503.03965 (2025)."

"Comment 2: Authors include CASP14 and CASP15 in their benchmark... It would be good to see the performance on CAMEO as well for the same period as ESM3."

"Comment 3: ...evaluating its performance on other downstream structure-based prediction tasks, such as GO-term prediction, could better illustrate the practical impact of the approach."

"[1] Yuan, Xinyu, et al. \"Protein structure tokenization: Benchmarking and new recipe.\" arXiv preprint arXiv:2503.00089 (2025)."

"[2] Lin, Zeming, et al. \"Evolutionary-scale prediction of atomic-level protein structure with a language model.\" Science 379.6637 (2023): 1123-1130."

"[3] Zhang, Zuobai, et al. \"Protein representation learning by geometric structure pretraining.\" arXiv preprint arXiv:2203.06125 (2022)."

"As the discussion period is coming to an end, we wanted to kindly check if our response has addressed your concerns. In particular, based on your suggestions, we have:"

We believe these updates strengthen the paper significantly and would love to hear your thoughts on these new results.

---

## 审稿人 MnGk ↔ 作者

### 📋 审稿人 MnGk 的主要意见

> This paper proposes PROTEINAE, a protein diffusion autoencoder mapping protein backbone coordinates from E(3) into a continuous, compact latent space for protein modeling and generation. PROTEINAE uses a non-equivariant Diffusion Transformer and is trained with a single flow matching objective to simplify the training objective. PROTEINAE achieves better reconstruction quality and high-quality structure generation that significantly outperforms prior latent-based methods.

> "[1] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" arXiv preprint arXiv:2503.00710 (2025) [2] Geffner, Tomas, et al. \"La-proteina: Atomistic protein generation via partially latent flow matching.\" arXiv preprint arXiv:2507.09466 (2025)."

> Please refer to the weakness section

### ✍️ 作者回复

"Comment 1: Structure-based method is still better than the latent-based model... Could authors elaborate more on that?"

These adjustments led to the improved results shown in the updated Table (see Comment 3 response).

"[1] Esser, Patrick, et al. \"Scaling rectified flow transformers for high-resolution image synthesis.\" Forty-first international conference on machine learning. 2024."

"[2] Zheng, Boyang, et al. \"Diffusion Transformers with Representation Autoencoders.\" arXiv preprint arXiv:2510.11690 (2025)."

"Comment 2: PROTEINAE doesn’t consider equivariance to simplify the design but would that lead to generating non-physical structures?"

"To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

"Comment 3: The comparison missed some important baselines, La-proteina and Proteina."

"As the discussion period is coming to an end, we wanted to kindly check if our response has addressed your concerns. In particular, based on your suggestions, we have:"

Your feedback on these additions would be very valuable to us. We hope these clarifications help address your concerns regarding the soundness and contribution of our work.

---

## 审稿人 qmAJ ↔ 作者

### 📋 审稿人 qmAJ 的主要意见

> Unlike prior approaches that depend on SE(3)-equivariant models, discrete tokenization, or multiple loss functions, PROTEINAE simplifies training with a single flow-matching objective and a non-equivariant Diffusion Transformer (DiT) architecture. The model efficiently encodes protein backbones into a latent space through a bottleneck design, enabling high-fidelity reconstruction and scalable downstream modeling. On benchmarks such as CASP14 and CASP15, PROTEINAE achieves state-of-the-art reconstruction accuracy, substantially outperforming discrete and equivariant autoencoders.

> The authors argue that strict equivariance may not be essential for effective protein representation learning, citing recent advances such as AlphaFold3 and Proteina, which also employ non-equivariant architectures. However, the paper could benefit from a more comprehensive discussion of related work on 3D protein autoencoder design, as well as a deeper theoretical justification for the choice of a non-equivariant model.

> This paper introduces a non-equivariant diffusion autoencoder that learns continuous protein structure representations directly from 3D coordinates, simplifying model design and training compared to SE(3)-equivariant or discrete approaches. But as mentioned before, the paper could benefit from a deeper theoretical justification for the choice of a non-equivariant model.

### ✍️ 作者回复

"Comment 1: This paper lacks sufficient discussion of prior work... For example, the model LatentDiff is compared in Table 2, but it is not discussed in the related-work section."

"[1] Fu, Cong, et al. \"A latent diffusion model for protein structure generation.\" Learning on graphs conference. PMLR, 2024."

"[2] Yim, Jason, et al. \"SE (3) diffusion model with application to protein backbone generation.\" arXiv preprint arXiv:2302.02277 (2023)."

"[3] Watson, Joseph L., et al. \"De novo design of protein structure and function with RFdiffusion.\" Nature 620.7976 (2023): 1089-1100."

"Comment 2: The authors argue that strict equivariance may not be essential... However, the paper would benefit from a deeper theoretical justification for choosing a non-equivariant model."

"Our perspective on the necessity of SE(3) equivariance distinguishes between two categories of tasks:"

"[2] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" ICLR 2025."

"[3] Zitnick, Larry, et al. \"Spherical channels for modeling atomic interactions.\" NeurIPS 2022: 8054-8067."

"[4] Ding, Yuhui, and Thomas Hofmann. \"Scalable Non-Equivariant 3D Molecule Generation via Rotational Alignment.\" ICML 2025."

"[8] Joshi, Chaitanya K., et al. \"All-atom diffusion transformers: Unified generative modelling of molecules and materials.\" arXiv preprint arXiv:2503.03965 (2025)."

"Though it is hard for us to give a fully theoretical proof why choosing a non-equivariant model, we can show that ProteinAE learns the approximate equivariance and could generate physically valid structures, as details following:"

"To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

"We wanted to confirm that we have updated the manuscript to address your specific points:"

We believe these additions improve the completeness and presentation of the paper. We would appreciate it if you could take a moment to check these updates.

---

## 审稿人 dnyu ↔ 作者

### 📋 审稿人 dnyu 的主要意见

> This paper proposes a new generative model for protein tertiary structure generation and reconstruction. Most existing approaches rely on coordinate prediction models or diffusion models based on stochastic noise denoising, which are computationally expensive and often struggle to maintain structural consistency and reconstruction accuracy. In contrast, this study combines the Flow Matching framework with a Transformer-based network, achieving continuous and stable structure generation. Unlike conventional SE(3)-equivariant models, the proposed method intentionally adopts a non-equivariant architecture on E(3) space. This design eliminates the need for explicit and computationally costly handling of rotations and translations, while still maintaining effective geometric robustness through structure alignment, pairwise bias based on relative distances and angles, and data augmentation.

> The proposed framework consists of three stages. In the first stage, the model takes the backbone atoms of each residue as input and compresses them into residue-level representations using an All-Atom Attention Encoder, which is designed to capture both spatial dependencies among residue pairs and primary sequence information. In the second stage, these features are processed by an Encoder–Decoder structure based on a Diffusion Transformer (DiT), which learns the global 3D correlations of the entire protein. Pairwise representations are incorporated as attention biases, enabling the model to encode global dependencies that reflect inter-residue distances and angles. The third stage introduces the Protein Latent Diffusion Model (PLDM), which treats the latent representations of residue sequences obtained by the encoder as latent token sequences. After compressing both the sequence length and feature dimension, PLDM learns the diffusion process directly in the latent space. Rather than performing stochastic noise denoising, PLDM is designed as a Transformer that predicts the velocity field of latent vectors based on Flow Matching. To preserve the sequential order while integrating temporal embeddings, positional encodings are applied to the latent tokens.

> Experimental evaluation on protein structures from the AlphaFold Database demonstrates that the proposed method achieves smoother and more stable structure generation than conventional diffusion models, with higher reconstruction accuracy as measured by RMSD and FAPE. The generated structures also preserve physical consistency, confirming that the proposed approach enables efficient and high-precision protein structure generation.

### ✍️ 作者回复

"Comment: Do the authors have any ideas or future plans for incorporating additional constraints or introducing some form of equivariant mechanism to extend the applicability of the proposed model to larger and more complex protein structures?"

Similarly, I believe the primary advantage of incorporating SE(3) equivariance lies in ligand modeling. Recent works, such as Pearl [1], have reintroduced SO(3) into the AlphaFold3 architecture, resulting in strong performance in ligand docking. However, this improvement could also be attributed to the contribution of synthetic data. Another approach involves using energy functions as potentials to guide the sampling process, as demonstrated by methods like Boltz-Steering [2] and Boltz-GSP [3], in order to denoise more valid structures. Nevertheless, further experimentation is required to validate these approaches.

"Furthermore, regarding the concern about geometric consistency in larger structures with our current non-equivariant design, our validation tests confirm that ProteinAE already achieves high geometric validity (Ramachandran, bond lengths/angles) and learns approximate equivariance effectively via data augmentation, as details following:"

"To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

Thank you again for your encouraging review and for recognizing the novelty of ProteinAE.

We are writing to ensure that our response regarding your questions. In our rebuttal, we outlined our plans to extend the model's applicability. We hope this explanation, along with our other updates, solidifies your positive assessment of our work. Please let us know if you have any further questions before the discussion period closes.

---

