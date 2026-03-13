# OpenReview 讨论总结

## 论文信息

**标题:** ProteinAE: Protein Diffusion Autoencoders for Structure Encoding

**作者:** Shaoning Li, Le Zhuo, Yusong Wang, Mingyu Li, Xinheng He, Fandi Wu, Hongsheng Li, Pheng-Ann Heng

**摘要:**
Developing effective representations of protein structures is essential for advancing protein science, particularly for protein generative modeling. Current approaches often grapple with the complexities of the math: SE ( 3 ) text: manifold, rely on discrete tokenization, or the need for multiple training objectives, all of which can hinder the model optimization and generalization. We introduce ProteinAE, a novel and streamlined protein diffusion autoencoder designed to overcome these challenges by directly mapping protein backbone coordinates from math: E ( 3 ) text: into a continuous, compact latent space. ProteinAE employs a non-equivariant Diffusion Transformer with a bottleneck design for efficient compression and is trained end-to-end with a single flow matching objective, substantially simplifying the optimization pipeline. We demonstrate that ProteinAE achieves state-of-the-art reconstruction quality, outperforming existing autoencoders. The resulting latent space serves as a powerful foundation for a latent diffusion model that bypasses the need for explicit equivariance. This enables efficient, high-quality structure generation that is competitive with leading structure-based approaches and significantly outperforms prior latent-based methods. Code is available at link "https://github.com/OnlyLoveKFC/ProteinAE_v1" [ref=e18]:
        - /url: https://github.com/OnlyLoveKFC/ProteinAE_v1 text: .

---

## 讨论总结

本文共收到 **21** 条评论/评审。

### 分类统计:

#### 决定 (1 条)

**1. Paper Decision**
- **作者:** Program Chairs
- **日期:** 26 Jan 2026, 16:42
- **内容:**

  - strong: Paper Decision
  - link "Revisions" [ref=e38] [nth=1]:
  - /url: /revisions?id=xxQiOs308c

  **Decision:**

  - button "Public Comment" [ref=e39] [nth=1]
  - group "Collapse controls":
  - button "−" [ref=e40] [nth=1]
  - button "＝" [ref=e41] [nth=1]
  - button "≡" [ref=e42] [nth=1]

---


#### 元评审 (1 条)

**1. Meta Review of Submission11944 by Area Chair x5kH**
- **日期:** 07 Jan 2026, 03:52
- **内容:**

  - link "Revisions" [ref=e45] [nth=2]:
  - /url: /revisions?id=AdCQpudtwZ

  **Summary:**


  **Reviewer Concerns:**


  Reviewers were concerned about model equivariance, and experimental data and comparison, and it seems most of them have been addressed.

  **Reviewer Scores:**

  The reviewer scores split between positive and negative.

  - button "Public Comment" [ref=e46] [nth=2]
  - group "Collapse controls":
  - button "−" [ref=e47] [nth=2]
  - button "＝" [ref=e48] [nth=2]
  - button "≡" [ref=e49] [nth=2]

---


#### 官方评论 (14 条)

**1. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 16:51
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e66] [nth=5]:
  - /url: /revisions?id=w8JkLnStFV

  **Comment:**

  - heading "Response to Reviewer FiwP" [ref=e67] [level=2]
  - blockquote:

  "Comment 1: In the introduction, authors mention that other models use SE(3) representations and are therefore slow. However, SE(3) representations are also essential in protein structure modeling specifically in generative protein design, so this point needs to be explained more carefully..."

  **Response: We thank the reviewer for raising this important point regarding the trade-offs of SE(3) equivariance.**


  - strong: AlphaFold 3
  - strong: Proteina
  - strong: SCN
  - strong: RADM
  - strong: ADiT
  - strong: scalable non-equivariant architectures

  "Our perspective on the necessity of SE(3) equivariance distinguishes between two categories of tasks:"

  - list:

  **Generation, Reconstruction, and Cross-modal Tasks (e.g., Folding/Inverse Folding):**

  - strong: ProteinAE learns approximate SE(3) equivariance

  **Physical Understanding and Force Fields (MLFF):**

  - emphasis: must
  - emphasis:
  - strong: cannot
  - emphasis: "Evidence:"
  - strong: 1B parameter Transformer
  - strong: 6M parameter EGNN
  - table:
  - rowgroup:
  - row "Model Energy MAE (meV) Forces MAE (meV/Å)":
  - columnheader "Model" [ref=e68]
  - columnheader "Energy MAE (meV)" [ref=e69]
  - columnheader "Forces MAE (meV/Å)" [ref=e70]
  - rowgroup:
  - row "eSEN-sm-d 6M 129.77 13.01":
  - cell "eSEN-sm-d 6M" [ref=e71]
  - cell "129.77" [ref=e72]
  - cell "13.01" [ref=e73]
  - row "Transformer 1B 117.99 18.35":
  - cell "Transformer 1B" [ref=e74]
  - cell "117.99" [ref=e75]
  - cell "18.35" [ref=e76]
  - button "Public Comment" [ref=e77] [nth=5]
  - group "Collapse controls":
  - button "−" [ref=e78] [nth=5]
  - button "＝" [ref=e79] [nth=5]
  - button "≡" [ref=e80] [nth=5]

---

**2. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 16:52
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e83] [nth=6]:
  - /url: /revisions?id=cbooM5Osxd

  **Comment:**


  **Experimental Verification of Equivariance:**

  - list:
  - math: E r ( x )
  - math: E r ( x ) = E x 1 ∼ p data R ∼ Unif ( SO ( 3 ) ) [ RMSD ( x ^ ( x 1 ) , R x ^ ( R ⊤ x 1 ) ) ]
  - math: E u ( x )
  - math: U
  - math: E u ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , U x ^ ( R ⊤ x 1 ) ) ]
  - math: E ( x )
  - math: E ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , x ^ ( R ⊤ x 1 ) ) ]
  - table:
  - rowgroup:
  - row "Model (Pass Rate) (Pass Rate) (Pass Rate)":
  - columnheader "Model" [ref=e84] [nth=1]
  - columnheader "(Pass Rate)" [ref=e85]:
  - math: E r
  - columnheader "(Pass Rate)" [ref=e86] [nth=1]:
  - math: E u
  - columnheader "(Pass Rate)" [ref=e87] [nth=2]:
  - math: E
  - rowgroup:
  - row "ESM3 VQ-VAE 0% 100% 100%":
  - cell "ESM3 VQ-VAE" [ref=e88]:
  - strong: ESM3 VQ-VAE
  - cell "0%" [ref=e89]
  - cell "100%" [ref=e90]
  - cell "100%" [ref=e91] [nth=1]
  - row "ProteinAE 100% 100% 0%":
  - cell "ProteinAE" [ref=e92]:
  - strong: ProteinAE
  - cell "100%" [ref=e93] [nth=2]
  - cell "100%" [ref=e94] [nth=3]
  - cell "0%" [ref=e95] [nth=1]

  **Analysis:**

  - math: E
  - math: E r
  - strong: invariant
  - math: E r
  - math: E
  - strong: equivariant
  - math: E u

  **References:**

  - emphasis: Nature

  "[2] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" ICLR 2025."
  "[3] Zitnick, Larry, et al. \"Spherical channels for modeling atomic interactions.\" NeurIPS 2022: 8054-8067."
  "[4] Ding, Yuhui, and Thomas Hofmann. \"Scalable Non-Equivariant 3D Molecule Generation via Rotational Alignment.\" ICML 2025."

  - emphasis: Science
  - emphasis: nature
  - emphasis: arXiv preprint arXiv:2510.02259

  "[8] Joshi, Chaitanya K., et al. \"All-atom diffusion transformers: Unified generative modelling of molecules and materials.\" arXiv preprint arXiv:2503.03965 (2025)."

  - separator
  - blockquote:

  "Comment 2: Authors include CASP14 and CASP15 in their benchmark... It would be good to see the performance on CAMEO as well for the same period as ESM3."

  **Response: We thank the reviewer for this valuable suggestion.**


  - strong: CAMEO 2022
  - table:
  - rowgroup:
  - row "Model CA RMSD (Å)":
  - columnheader "Model" [ref=e96] [nth=2]
  - columnheader "CA RMSD (Å)" [ref=e97]
  - rowgroup:
  - row "ESM3 VQ-VAE 1.08 ± 1.76":
  - cell "ESM3 VQ-VAE" [ref=e98] [nth=1]
  - cell "1.08 ± 1.76" [ref=e99]
  - row "DPLM-2 650M 1.92 ± 1.45":
  - cell "DPLM-2 650M" [ref=e100]
  - cell "1.92 ± 1.45" [ref=e101]
  - row "ProteinAE 0.20 ± 0.19":
  - cell "ProteinAE" [ref=e102] [nth=1]:
  - strong: ProteinAE
  - cell "0.20 ± 0.19" [ref=e103]:
  - strong: 0.20 ± 0.19
  - button "Public Comment" [ref=e104] [nth=6]
  - group "Collapse controls":
  - button "−" [ref=e105] [nth=6]
  - button "＝" [ref=e106] [nth=6]
  - button "≡" [ref=e107] [nth=6]

---

**3. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 16:52
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e110] [nth=7]:
  - /url: /revisions?id=J9kXnloOjd

  **Comment:**

  - blockquote:

  "Comment 3: ...evaluating its performance on other downstream structure-based prediction tasks, such as GO-term prediction, could better illustrate the practical impact of the approach."

  **Response: We appreciate the reviewer for pointing this out.**


  - strong: StructTokBench
  - emphasis: Xinyu et al.
  - strong: Bind
  - strong: Cat
  - strong: Con
  - table:
  - rowgroup:
  - row "Task Split FoldSeek ProTokens ESM3 VanillaVQ AminoAseed ProteinAE":
  - columnheader "Task" [ref=e111]
  - columnheader "Split" [ref=e112]
  - columnheader "FoldSeek" [ref=e113]
  - columnheader "ProTokens" [ref=e114]
  - columnheader "ESM3" [ref=e115]
  - columnheader "VanillaVQ" [ref=e116]
  - columnheader "AminoAseed" [ref=e117]
  - columnheader "ProteinAE" [ref=e118]:
  - strong: ProteinAE
  - rowgroup:
  - row "BindBio Fold 52.37 58.47 62.84 62.02 65.73 73.97":
  - cell "BindBio" [ref=e119]:
  - strong: BindBio
  - cell "Fold" [ref=e120]
  - cell "52.37" [ref=e121]
  - cell "58.47" [ref=e122]
  - cell "62.84" [ref=e123]
  - cell "62.02" [ref=e124]
  - cell "65.73" [ref=e125]
  - cell "73.97" [ref=e126]:

  **73.97**

  - row "SupFam 52.41 60.47 65.22 62.92 68.30 74.56":
  - cell
  - cell "SupFam" [ref=e127]
  - cell "52.41" [ref=e128]
  - cell "60.47" [ref=e129]
  - cell "65.22" [ref=e130]
  - cell "62.92" [ref=e131]
  - cell "68.30" [ref=e132]
  - cell "74.56" [ref=e133]:

  **74.56**

  - row "BindInt Fold 53.18 44.66 44.30 47.25 47.11 46.24":
  - cell "BindInt" [ref=e134]:
  - strong: BindInt
  - cell "Fold" [ref=e135] [nth=1]
  - cell "53.18" [ref=e136]
  - cell "44.66" [ref=e137]
  - cell "44.30" [ref=e138]
  - cell "47.25" [ref=e139]
  - cell "47.11" [ref=e140]
  - cell "46.24" [ref=e141]
  - row "SupFam 46.20 86.05 90.77 86.71 90.53 90.62":
  - cell
  - cell "SupFam" [ref=e142] [nth=1]
  - cell "46.20" [ref=e143]
  - cell "86.05" [ref=e144]
  - cell "90.77" [ref=e145]
  - cell "86.71" [ref=e146]
  - cell "90.53" [ref=e147]
  - cell "90.62" [ref=e148]:

  **90.62**

  - row "BindShake Org 53.40 59.82 66.10 67.04 69.61 74.68":
  - cell "BindShake" [ref=e149]:
  - strong: BindShake
  - cell "Org" [ref=e150]
  - cell "53.40" [ref=e151]
  - cell "59.82" [ref=e152]
  - cell "66.10" [ref=e153]
  - cell "67.04" [ref=e154]
  - cell "69.61" [ref=e155]
  - cell "74.68" [ref=e156]:

  **74.68**

  - row "CatInt Fold 53.43 58.16 61.09 58.89 62.19 60.50":
  - cell "CatInt" [ref=e157]:
  - strong: CatInt
  - cell "Fold" [ref=e158] [nth=2]
  - cell "53.43" [ref=e159]
  - cell "58.16" [ref=e160]
  - cell "61.09" [ref=e161]
  - cell "58.89" [ref=e162]
  - cell "62.19" [ref=e163]
  - cell "60.50" [ref=e164]
  - row "SupFam 51.41 83.85 89.82 85.00 91.91 90.59":
  - cell
  - cell "SupFam" [ref=e165] [nth=2]
  - cell "51.41" [ref=e166]
  - cell "83.85" [ref=e167]
  - cell "89.82" [ref=e168]
  - cell "85.00" [ref=e169]
  - cell "91.91" [ref=e170]
  - cell "90.59" [ref=e171]
  - row "CatBio Fold 56.37 56.14 65.33 67.58 65.95 79.74":
  - cell "CatBio" [ref=e172]:
  - strong: CatBio
  - cell "Fold" [ref=e173] [nth=3]
  - cell "56.37" [ref=e174]
  - cell "56.14" [ref=e175]
  - cell "65.33" [ref=e176]
  - cell "67.58" [ref=e177]
  - cell "65.95" [ref=e178]
  - cell "79.74" [ref=e179]:

  **79.74**

  - row "SupFam 53.78 64.05 74.65 70.92 87.59 89.13":
  - cell
  - cell "SupFam" [ref=e180] [nth=3]
  - cell "53.78" [ref=e181]
  - cell "64.05" [ref=e182]
  - cell "74.65" [ref=e183]
  - cell "70.92" [ref=e184]
  - cell "87.59" [ref=e185]
  - cell "89.13" [ref=e186]:

  **89.13**

  - row "Con Fold 49.26 56.23 55.22 56.98 57.23 59.50":
  - cell "Con" [ref=e187]:
  - strong: Con
  - cell "Fold" [ref=e188] [nth=4]
  - cell "49.26" [ref=e189]
  - cell "56.23" [ref=e190]
  - cell "55.22" [ref=e191]
  - cell "56.98" [ref=e192]
  - cell "57.23" [ref=e193]
  - cell "59.50" [ref=e194]:

  **59.50**

  - row "SupFam 51.39 74.33 80.53 74.60 86.60 81.89":
  - cell
  - cell "SupFam" [ref=e195] [nth=4]
  - cell "51.39" [ref=e196]
  - cell "74.33" [ref=e197]
  - cell "80.53" [ref=e198]
  - cell "74.60" [ref=e199]
  - cell "86.60" [ref=e200]
  - cell "81.89" [ref=e201]
  - row "Average AUROC% 52.11 63.84 68.72 67.26 72.07 74.67":
  - cell "Average" [ref=e202]:
  - strong: Average
  - cell "AUROC%" [ref=e203]:
  - strong: AUROC%
  - cell "52.11" [ref=e204]:

  **52.11**

  - cell "63.84" [ref=e205]:

  **63.84**

  - cell "68.72" [ref=e206]:

  **68.72**

  - cell "67.26" [ref=e207]:

  **67.26**

  - cell "72.07" [ref=e208]:

  **72.07**

  - cell "74.67" [ref=e209]:

  **74.67**

  - separator

  "[1] Yuan, Xinyu, et al. \"Protein structure tokenization: Benchmarking and new recipe.\" arXiv preprint arXiv:2503.00089 (2025)."
  "[2] Lin, Zeming, et al. \"Evolutionary-scale prediction of atomic-level protein structure with a language model.\" Science 379.6637 (2023): 1123-1130."
  "[3] Zhang, Zuobai, et al. \"Protein representation learning by geometric structure pretraining.\" arXiv preprint arXiv:2203.06125 (2022)."

  - button "Public Comment" [ref=e210] [nth=7]
  - group "Collapse controls":
  - button "−" [ref=e211] [nth=7]
  - button "＝" [ref=e212] [nth=7]
  - button "≡" [ref=e213] [nth=7]
  - heading "Replying to Official Comment by Authors" [ref=e214] [level=5]

---

**4. Official Comment by Authors**
- **内容:**

  **Comment:**

  Dear Reviewer FiwP,
  Thank you again for your constructive feedback.
  "As the discussion period is coming to an end, we wanted to kindly check if our response has addressed your concerns. In particular, based on your suggestions, we have:"

  - list:
  - strong: Clarified the SE(3) trade-off
  - strong: Added CAMEO Benchmarks
  - strong: Expanded Downstream Tasks

  We believe these updates strengthen the paper significantly and would love to hear your thoughts on these new results.
  Best regards, The Authors

  - button "Public Comment" [ref=e217] [nth=8]
  - group "Collapse controls":
  - button "−" [ref=e218] [nth=8]
  - button "＝" [ref=e219] [nth=8]
  - button "≡" [ref=e220] [nth=8]

---

**5. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 16:57
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e230] [nth=9]:
  - /url: /revisions?id=jr1qbG8xUh

  **Comment:**

  - heading "Response to Reviewer MnGk" [ref=e231] [level=2]
  - blockquote:

  "Comment 1: Structure-based method is still better than the latent-based model... Could authors elaborate more on that?"

  **Response: We thank the reviewer for this critical observation, which motivated us to refine our approach.**


  - list:

  **Time Shift in Flow Matching:**

  - math: x 0
  - math: x 1
  - math: S
  - math: t
  - math: x t = ( 1 − t ) x 0 + t x 1
  - math: t
  - math: t = t ( S − t ( S − 1 ) )
  - strong:
  - math: S = 12
  - math: t > 0.2
  - math: t < 0.2
  - list:

  **Dimension Scaling:**

  - strong: 768 to 1152

  These adjustments led to the improved results shown in the updated Table (see Comment 3 response).
  "[1] Esser, Patrick, et al. \"Scaling rectified flow transformers for high-resolution image synthesis.\" Forty-first international conference on machine learning. 2024."
  "[2] Zheng, Boyang, et al. \"Diffusion Transformers with Representation Autoencoders.\" arXiv preprint arXiv:2510.11690 (2025)."

  - separator
  - blockquote:

  "Comment 2: PROTEINAE doesn’t consider equivariance to simplify the design but would that lead to generating non-physical structures?"

  **Response: We appreciate the reviewer raising this valid concern regarding physical plausibility.**


  - strong: Equivariance Tests
  - strong: Geometric Validity Checks

  **1. Equivariance Test:**


  "To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

  - list:
  - math: E r ( x )
  - math: E r ( x ) = E x 1 ∼ p data R ∼ Unif ( SO ( 3 ) ) [ RMSD ( x ^ ( x 1 ) , R x ^ ( R ⊤ x 1 ) ) ]
  - math: E u ( x )
  - math: U
  - math: E u ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , U x ^ ( R ⊤ x 1 ) ) ]
  - math: E ( x )
  - math: E ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , x ^ ( R ⊤ x 1 ) ) ]
  - table:
  - rowgroup:
  - row "Model (Pass Rate) (Pass Rate) (Pass Rate)":
  - columnheader "Model" [ref=e232] [nth=3]
  - columnheader "(Pass Rate)" [ref=e233] [nth=3]:
  - math: E r
  - columnheader "(Pass Rate)" [ref=e234] [nth=4]:
  - math: E u
  - columnheader "(Pass Rate)" [ref=e235] [nth=5]:
  - math: E
  - rowgroup:
  - row "ESM3 VQ-VAE 0% 100% 100%":
  - cell "ESM3 VQ-VAE" [ref=e236] [nth=2]:
  - strong: ESM3 VQ-VAE
  - cell "0%" [ref=e237] [nth=2]
  - cell "100%" [ref=e238] [nth=4]
  - cell "100%" [ref=e239] [nth=5]
  - row "ProteinAE 100% 100% 0%":
  - cell "ProteinAE" [ref=e240] [nth=2]:
  - strong: ProteinAE
  - cell "100%" [ref=e241] [nth=6]
  - cell "100%" [ref=e242] [nth=7]
  - cell "0%" [ref=e243] [nth=3]

  **Analysis:**

  - math: E
  - math: E r
  - strong: invariant
  - math: E r
  - math: E
  - strong: equivariant
  - math: E u

  **2. Geometric Validity Check:**

  - code: stereo_chemical_props.txt
  - table:
  - rowgroup:
  - row "Parameter Atoms Min Max":
  - columnheader "Parameter" [ref=e244]
  - columnheader "Atoms" [ref=e245]
  - columnheader "Min" [ref=e246]
  - columnheader "Max" [ref=e247]
  - rowgroup:
  - row "Backbone - -180 180":
  - cell "Backbone" [ref=e248]:
  - strong:
  - math: ϕ , ψ
  - cell "-" [ref=e249]
  - cell "-180" [ref=e250]
  - cell "180" [ref=e251]
  - row "Bond Length (Å) N - CA 1.399 1.519":
  - cell "Bond Length (Å)" [ref=e252]:
  - strong: Bond Length (Å)
  - cell "N - CA" [ref=e253]
  - cell "1.399" [ref=e254]
  - cell "1.519" [ref=e255]
  - row "CA - C 1.447 1.603":
  - cell
  - cell "CA - C" [ref=e256]
  - cell "1.447" [ref=e257]
  - cell "1.603" [ref=e258]
  - row "C - N 1.280 1.380":
  - cell
  - cell "C - N" [ref=e259]
  - cell "1.280" [ref=e260]
  - cell "1.380" [ref=e261]
  - row "C - O 1.172 1.286":
  - cell
  - cell "C - O" [ref=e262]
  - cell "1.172" [ref=e263]
  - cell "1.286" [ref=e264]
  - row "Bond Angle (°) N - CA - C 102.9 119.1":
  - cell "Bond Angle (°)" [ref=e265]:
  - strong: Bond Angle (°)
  - cell "N - CA - C" [ref=e266]
  - cell "102.9" [ref=e267]
  - cell "119.1" [ref=e268]
  - row "CA - C - N 113.7 126.3":
  - cell
  - cell "CA - C - N" [ref=e269]
  - cell "113.7" [ref=e270]
  - cell "126.3" [ref=e271]
  - row "C - N - CA 113.7 132.3":
  - cell
  - cell "C - N - CA" [ref=e272]
  - cell "113.7" [ref=e273] [nth=1]
  - cell "132.3" [ref=e274]
  - row "CA - C - O 113.8 126.4":
  - cell
  - cell "CA - C - O" [ref=e275]
  - cell "113.8" [ref=e276]
  - cell "126.4" [ref=e277]
  - table:
  - rowgroup:
  - row "Metric Type Violation Ratio (%)":
  - columnheader "Metric" [ref=e278]
  - columnheader "Type" [ref=e279]
  - columnheader "Violation Ratio (%)" [ref=e280]
  - rowgroup:
  - row "Ramachandran 0.00":
  - cell "Ramachandran" [ref=e281]:
  - strong: Ramachandran
  - cell:
  - math: ϕ , ψ
  - cell "0.00" [ref=e282]:

  **0.00**

  - row "Bond Lengths N-CA, CA-C, C-N, C-O 1.24":
  - cell "Bond Lengths" [ref=e283]:
  - strong: Bond Lengths
  - cell "N-CA, CA-C, C-N, C-O" [ref=e284]
  - cell "1.24" [ref=e285]:

  **1.24**

  - row "Bond Angles N-CA-C, CA-C-N, C-N-CA, CA-C-O 1.10":
  - cell "Bond Angles" [ref=e286]:
  - strong: Bond Angles
  - cell "N-CA-C, CA-C-N, C-N-CA, CA-C-O" [ref=e287]
  - cell "1.10" [ref=e288]:

  **1.10**

  - row "Atom Clashes No Overlap 0.00":
  - cell "Atom Clashes" [ref=e289]:
  - strong: Atom Clashes
  - cell "No Overlap" [ref=e290]
  - cell "0.00" [ref=e291] [nth=1]:

  **0.00**

  - row "Left-hand Alpha Helix - 0.00":
  - cell "Left-hand Alpha Helix" [ref=e292]:
  - strong: Left-hand Alpha Helix
  - cell "-" [ref=e293] [nth=1]
  - cell "0.00" [ref=e294] [nth=2]:

  **0.00**

  - emphasis: "Note: Small violation ratios (approx. 1%) are expected as even ground truth structures in AFDB contain minor outliers."
  - button "Public Comment" [ref=e295] [nth=10]
  - group "Collapse controls":
  - button "−" [ref=e296] [nth=10]
  - button "＝" [ref=e297] [nth=10]
  - button "≡" [ref=e298] [nth=10]

---

**6. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 16:58
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e301] [nth=10]:
  - /url: /revisions?id=t3ArpqIhQo

  **Comment:**

  - blockquote:

  "Comment 3: The comparison missed some important baselines, La-proteina and Proteina."

  **Response: We thank the reviewer for identifying these missing baselines.**


  - strong: Proteina
  - math: C α

  **Updated Generation Benchmark:**

  - table:
  - rowgroup:
  - row "Type Method Des ( ) Div ( )":
  - columnheader "Type" [ref=e302] [nth=1]
  - columnheader "Method" [ref=e303]
  - columnheader "Des ( )" [ref=e304]:
  - math: ↑
  - columnheader "Div ( )" [ref=e305]:
  - math: ↑
  - rowgroup:
  - row "SDM RFdiffusion (Watson et al., 2023) 96% 247":
  - cell "SDM" [ref=e306]:
  - strong: SDM
  - cell "RFdiffusion (Watson et al., 2023)" [ref=e307]
  - cell "96%" [ref=e308]
  - cell "247" [ref=e309]
  - row "ProteinSGM (Lee et al., 2023) 49% 122":
  - cell
  - cell "ProteinSGM (Lee et al., 2023)" [ref=e310]
  - cell "49%" [ref=e311]
  - cell "122" [ref=e312]
  - row "FrameFlow PDB (Yim et al., 2023a) 91% 278":
  - cell
  - cell "FrameFlow PDB (Yim et al., 2023a)" [ref=e313]
  - cell "91%" [ref=e314]
  - cell "278" [ref=e315]
  - row "FrameFlow AFDB 23% 54":
  - cell
  - cell "FrameFlow AFDB" [ref=e316]
  - cell "23%" [ref=e317]
  - cell "54" [ref=e318]
  - row "Proteina 200M 94% 228":
  - cell
  - cell "Proteina 200M" [ref=e319]:
  - math: D F S
  - cell "94%" [ref=e320]
  - cell "228" [ref=e321]
  - row "MLLM ESM3 (Hayes et al., 2025) 61% 127":
  - cell "MLLM" [ref=e322]:
  - strong: MLLM
  - cell "ESM3 (Hayes et al., 2025)" [ref=e323]
  - cell "61%" [ref=e324]
  - cell "127" [ref=e325]
  - row "DPLM-2 650M (Wang et al., 2024) 63% 130":
  - cell
  - cell "DPLM-2 650M (Wang et al., 2024)" [ref=e326]
  - cell "63%" [ref=e327]
  - cell "130" [ref=e328]
  - row "semi-LDM LSD (Yim et al., 2025) 69% 203":
  - cell "semi-LDM" [ref=e329]:
  - strong: semi-LDM
  - cell "LSD (Yim et al., 2025)" [ref=e330]
  - cell "69%" [ref=e331]
  - cell "203" [ref=e332]
  - row "LDM LatentDiff (Fu et al., 2024) 17% 34":
  - cell "LDM" [ref=e333]:
  - strong: LDM
  - cell "LatentDiff (Fu et al., 2024)" [ref=e334]
  - cell "17%" [ref=e335]
  - cell "34" [ref=e336]
  - row "PROTEINAE-PLDM-shift ( ) 95% 251":
  - cell
  - cell "PROTEINAE-PLDM-shift ( )" [ref=e337]:
  - math: γ = 0.5
  - cell "95%" [ref=e338]
  - cell "251" [ref=e339]
  - button "Public Comment" [ref=e340] [nth=11]
  - group "Collapse controls":
  - button "−" [ref=e341] [nth=11]
  - button "＝" [ref=e342] [nth=11]
  - button "≡" [ref=e343] [nth=11]
  - heading "Replying to Official Comment by Authors" [ref=e344] [nth=1] [level=5]

---

**7. Official Comment by Authors**
- **内容:**

  **Comment:**

  Dear Reviewer MnGk,
  Thank you again for your constructive feedback.
  "As the discussion period is coming to an end, we wanted to kindly check if our response has addressed your concerns. In particular, based on your suggestions, we have:"

  - list:
  - strong: Included Missing Baselines
  - strong: Addressed Physical Consistency

  Your feedback on these additions would be very valuable to us. We hope these clarifications help address your concerns regarding the soundness and contribution of our work.
  Best regards, The Authors

  - button "Public Comment" [ref=e347] [nth=12]
  - group "Collapse controls":
  - button "−" [ref=e348] [nth=12]
  - button "＝" [ref=e349] [nth=12]
  - button "≡" [ref=e350] [nth=12]

---

**8. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 17:13
- **内容:**

  - strong: Official Comment by Authors
  - link "Revisions" [ref=e360] [nth=12]:
  - /url: /revisions?id=iJm1OYsXuO

  **Comment:**

  - heading "Response to Reviewer dnyu" [ref=e361] [level=2]
  - blockquote:

  "Comment: Do the authors have any ideas or future plans for incorporating additional constraints or introducing some form of equivariant mechanism to extend the applicability of the proposed model to larger and more complex protein structures?"

  **Response: We truly appreciate the reviewer's recognition of our work and share the same vision regarding these limitations.**


  - strong: ProteinAE v2, which addresses these specific limitations
  - strong: visualization results
  - strong: Appendix (ProteinAE v2 Preview) Fig 5

  Similarly, I believe the primary advantage of incorporating SE(3) equivariance lies in ligand modeling. Recent works, such as Pearl [1], have reintroduced SO(3) into the AlphaFold3 architecture, resulting in strong performance in ligand docking. However, this improvement could also be attributed to the contribution of synthetic data. Another approach involves using energy functions as potentials to guide the sampling process, as demonstrated by methods like Boltz-Steering [2] and Boltz-GSP [3], in order to denoise more valid structures. Nevertheless, further experimentation is required to validate these approaches.

  - emphasis: arXiv preprint arXiv:2510.24670
  - emphasis: BioRxiv
  - emphasis: arXiv preprint arXiv:2510.08946

  "Furthermore, regarding the concern about geometric consistency in larger structures with our current non-equivariant design, our validation tests confirm that ProteinAE already achieves high geometric validity (Ramachandran, bond lengths/angles) and learns approximate equivariance effectively via data augmentation, as details following:"

  - button "Public Comment" [ref=e362] [nth=14]
  - group "Collapse controls":
  - button "−" [ref=e363] [nth=14]
  - button "＝" [ref=e364] [nth=14]
  - button "≡" [ref=e365] [nth=14]
  - heading "Replying to Official Comment by Authors" [ref=e366] [nth=2] [level=5]

---

**9. Official Comment by Authors**
- **内容:**

  - strong: Official Comment by Authors

  **Comment:**


  **1. Equivariance Test:**


  "To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

  - list:
  - math: E r ( x )
  - math: E r ( x ) = E x 1 ∼ p data R ∼ Unif ( SO ( 3 ) ) [ RMSD ( x ^ ( x 1 ) , R x ^ ( R ⊤ x 1 ) ) ]
  - math: E u ( x )
  - math: U
  - math: E u ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , U x ^ ( R ⊤ x 1 ) ) ]
  - math: E ( x )
  - math: E ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , x ^ ( R ⊤ x 1 ) ) ]
  - table:
  - rowgroup:
  - row "Model (Pass Rate) (Pass Rate) (Pass Rate)":
  - columnheader "Model" [ref=e369] [nth=4]
  - columnheader "(Pass Rate)" [ref=e370] [nth=6]:
  - math: E r
  - columnheader "(Pass Rate)" [ref=e371] [nth=7]:
  - math: E u
  - columnheader "(Pass Rate)" [ref=e372] [nth=8]:
  - math: E
  - rowgroup:
  - row "ESM3 VQ-VAE 0% 100% 100%":
  - cell "ESM3 VQ-VAE" [ref=e373] [nth=3]:
  - strong: ESM3 VQ-VAE
  - cell "0%" [ref=e374] [nth=4]
  - cell "100%" [ref=e375] [nth=8]
  - cell "100%" [ref=e376] [nth=9]
  - row "ProteinAE 100% 100% 0%":
  - cell "ProteinAE" [ref=e377] [nth=3]:
  - strong: ProteinAE
  - cell "100%" [ref=e378] [nth=10]
  - cell "100%" [ref=e379] [nth=11]
  - cell "0%" [ref=e380] [nth=5]

  **Analysis:**

  - math: E
  - math: E r
  - strong: invariant
  - math: E r
  - math: E
  - strong: equivariant
  - math: E u

  **2. Geometric Validity Check:**

  - code: stereo_chemical_props.txt
  - table:
  - rowgroup:
  - row "Parameter Atoms Min Max":
  - columnheader "Parameter" [ref=e381] [nth=1]
  - columnheader "Atoms" [ref=e382] [nth=1]
  - columnheader "Min" [ref=e383] [nth=1]
  - columnheader "Max" [ref=e384] [nth=1]
  - rowgroup:
  - row "Backbone - -180 180":
  - cell "Backbone" [ref=e385] [nth=1]:
  - strong:
  - math: ϕ , ψ
  - cell "-" [ref=e386] [nth=2]
  - cell "-180" [ref=e387] [nth=1]
  - cell "180" [ref=e388] [nth=1]
  - row "Bond Length (Å) N - CA 1.399 1.519":
  - cell "Bond Length (Å)" [ref=e389] [nth=1]:
  - strong: Bond Length (Å)
  - cell "N - CA" [ref=e390] [nth=1]
  - cell "1.399" [ref=e391] [nth=1]
  - cell "1.519" [ref=e392] [nth=1]
  - row "CA - C 1.447 1.603":
  - cell
  - cell "CA - C" [ref=e393] [nth=1]
  - cell "1.447" [ref=e394] [nth=1]
  - cell "1.603" [ref=e395] [nth=1]
  - row "C - N 1.280 1.380":
  - cell
  - cell "C - N" [ref=e396] [nth=1]
  - cell "1.280" [ref=e397] [nth=1]
  - cell "1.380" [ref=e398] [nth=1]
  - row "C - O 1.172 1.286":
  - cell
  - cell "C - O" [ref=e399] [nth=1]
  - cell "1.172" [ref=e400] [nth=1]
  - cell "1.286" [ref=e401] [nth=1]
  - row "Bond Angle (°) N - CA - C 102.9 119.1":
  - cell "Bond Angle (°)" [ref=e402] [nth=1]:
  - strong: Bond Angle (°)
  - cell "N - CA - C" [ref=e403] [nth=1]
  - cell "102.9" [ref=e404] [nth=1]
  - cell "119.1" [ref=e405] [nth=1]
  - row "CA - C - N 113.7 126.3":
  - cell
  - cell "CA - C - N" [ref=e406] [nth=1]
  - cell "113.7" [ref=e407] [nth=2]
  - cell "126.3" [ref=e408] [nth=1]
  - row "C - N - CA 113.7 132.3":
  - cell
  - cell "C - N - CA" [ref=e409] [nth=1]
  - cell "113.7" [ref=e410] [nth=3]
  - cell "132.3" [ref=e411] [nth=1]
  - row "CA - C - O 113.8 126.4":
  - cell
  - cell "CA - C - O" [ref=e412] [nth=1]
  - cell "113.8" [ref=e413] [nth=1]
  - cell "126.4" [ref=e414] [nth=1]
  - table:
  - rowgroup:
  - row "Metric Type Violation Ratio (%)":
  - columnheader "Metric" [ref=e415] [nth=1]
  - columnheader "Type" [ref=e416] [nth=2]
  - columnheader "Violation Ratio (%)" [ref=e417] [nth=1]
  - rowgroup:
  - row "Ramachandran 0.00":
  - cell "Ramachandran" [ref=e418] [nth=1]:
  - strong: Ramachandran
  - cell:
  - math: ϕ , ψ
  - cell "0.00" [ref=e419] [nth=3]:

  **0.00**

  - row "Bond Lengths N-CA, CA-C, C-N, C-O 1.24":
  - cell "Bond Lengths" [ref=e420] [nth=1]:
  - strong: Bond Lengths
  - cell "N-CA, CA-C, C-N, C-O" [ref=e421] [nth=1]
  - cell "1.24" [ref=e422] [nth=1]:

  **1.24**

  - row "Bond Angles N-CA-C, CA-C-N, C-N-CA, CA-C-O 1.10":
  - cell "Bond Angles" [ref=e423] [nth=1]:
  - strong: Bond Angles
  - cell "N-CA-C, CA-C-N, C-N-CA, CA-C-O" [ref=e424] [nth=1]
  - cell "1.10" [ref=e425] [nth=1]:

  **1.10**

  - row "Atom Clashes No Overlap 0.00":
  - cell "Atom Clashes" [ref=e426] [nth=1]:
  - strong: Atom Clashes
  - cell "No Overlap" [ref=e427] [nth=1]
  - cell "0.00" [ref=e428] [nth=4]:

  **0.00**

  - row "Left-hand Alpha Helix - 0.00":
  - cell "Left-hand Alpha Helix" [ref=e429] [nth=1]:
  - strong: Left-hand Alpha Helix
  - cell "-" [ref=e430] [nth=3]
  - cell "0.00" [ref=e431] [nth=5]:

  **0.00**

  - emphasis: "Note: Small violation ratios (approx. 1%) are expected as even ground truth structures in AFDB contain minor outliers."
  - button "Public Comment" [ref=e432] [nth=15]
  - group "Collapse controls":
  - button "−" [ref=e433] [nth=15]
  - button "＝" [ref=e434] [nth=15]
  - button "≡" [ref=e435] [nth=15]
  - heading "Replying to Official Comment by Authors" [ref=e436] [nth=3] [level=5]

---

**10. Official Comment by Authors**
- **内容:**

  **Comment:**

  Dear Reviewer dnyu,
  Thank you again for your encouraging review and for recognizing the novelty of ProteinAE.
  We are writing to ensure that our response regarding your questions. In our rebuttal, we outlined our plans to extend the model's applicability. We hope this explanation, along with our other updates, solidifies your positive assessment of our work. Please let us know if you have any further questions before the discussion period closes.
  Best regards, The Authors

  - button "Public Comment" [ref=e439] [nth=16]
  - group "Collapse controls":
  - button "−" [ref=e440] [nth=16]
  - button "＝" [ref=e441] [nth=16]
  - button "≡" [ref=e442] [nth=16]

---

**11. Official Comment by Authors**
- **内容:**

  - strong: Official Comment by Authors

  **Comment:**

  - heading "Response to Reviewer qmAJ" [ref=e454] [level=2]
  - blockquote:

  "Comment 1: This paper lacks sufficient discussion of prior work... For example, the model LatentDiff is compared in Table 2, but it is not discussed in the related-work section."

  **Response: We apologize for this oversight and thank the reviewer for bringing LatentDiff to our attention.**


  - strong: Latent Space Generative Models for Proteins.
  - strong: Fu et al. (2023)
  - strong: LatentDiff

  "[1] Fu, Cong, et al. \"A latent diffusion model for protein structure generation.\" Learning on graphs conference. PMLR, 2024."
  "[2] Yim, Jason, et al. \"SE (3) diffusion model with application to protein backbone generation.\" arXiv preprint arXiv:2302.02277 (2023)."
  "[3] Watson, Joseph L., et al. \"De novo design of protein structure and function with RFdiffusion.\" Nature 620.7976 (2023): 1089-1100."

  - button "Public Comment" [ref=e455] [nth=18]
  - group "Collapse controls":
  - button "−" [ref=e456] [nth=18]
  - button "＝" [ref=e457] [nth=18]
  - button "≡" [ref=e458] [nth=18]

---

**12. Official Comment by Authors**
- **作者:** Authors
- **日期:** 19 Nov 2025, 17:28
- **内容:**

  - link "Revisions" [ref=e461] [nth=14]:
  - /url: /revisions?id=mtP4UoxI0K

  **Comment:**

  - blockquote:

  "Comment 2: The authors argue that strict equivariance may not be essential... However, the paper would benefit from a deeper theoretical justification for choosing a non-equivariant model."

  **Response: We appreciate the opportunity to clarify our motivations.**


  - strong: AlphaFold 3
  - strong: Proteina
  - strong: SCN
  - strong: RADM
  - strong: ADiT
  - strong: scalable non-equivariant architectures

  "Our perspective on the necessity of SE(3) equivariance distinguishes between two categories of tasks:"

  - list:

  **Generation, Reconstruction, and Cross-modal Tasks (e.g., Folding/Inverse Folding):**

  - strong: ProteinAE learns approximate SE(3) equivariance

  **Physical Understanding and Force Fields (MLFF):**

  - emphasis: must
  - emphasis:
  - strong: cannot
  - emphasis: "Evidence:"
  - strong: 1B parameter Transformer
  - strong: 6M parameter EGNN
  - table:
  - rowgroup:
  - row "Model Energy MAE (meV) Forces MAE (meV/Å)":
  - columnheader "Model" [ref=e462] [nth=5]
  - columnheader "Energy MAE (meV)" [ref=e463] [nth=1]
  - columnheader "Forces MAE (meV/Å)" [ref=e464] [nth=1]
  - rowgroup:
  - row "eSEN-sm-d 6M 129.77 13.01":
  - cell "eSEN-sm-d 6M" [ref=e465] [nth=1]
  - cell "129.77" [ref=e466] [nth=1]
  - cell "13.01" [ref=e467] [nth=1]
  - row "Transformer 1B 117.99 18.35":
  - cell "Transformer 1B" [ref=e468] [nth=1]
  - cell "117.99" [ref=e469] [nth=1]
  - cell "18.35" [ref=e470] [nth=1]

  **References:**

  - emphasis: Nature

  "[2] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" ICLR 2025."
  "[3] Zitnick, Larry, et al. \"Spherical channels for modeling atomic interactions.\" NeurIPS 2022: 8054-8067."
  "[4] Ding, Yuhui, and Thomas Hofmann. \"Scalable Non-Equivariant 3D Molecule Generation via Rotational Alignment.\" ICML 2025."

  - emphasis: Science
  - emphasis: nature
  - emphasis: arXiv preprint arXiv:2510.02259

  "[8] Joshi, Chaitanya K., et al. \"All-atom diffusion transformers: Unified generative modelling of molecules and materials.\" arXiv preprint arXiv:2503.03965 (2025)."

  - button "Public Comment" [ref=e471] [nth=19]
  - group "Collapse controls":
  - button "−" [ref=e472] [nth=19]
  - button "＝" [ref=e473] [nth=19]
  - button "≡" [ref=e474] [nth=19]
  - heading "Replying to Official Comment by Authors" [ref=e475] [nth=4] [level=5]

---

**13. Official Comment by Authors**
- **内容:**

  **Comment:**

  "Though it is hard for us to give a fully theoretical proof why choosing a non-equivariant model, we can show that ProteinAE learns the approximate equivariance and could generate physically valid structures, as details following:"

  **1. Equivariance Test:**

  "To validate our claim, we tested ProteinAE against ESM3 VQ-VAE on proteins of varying lengths (100-500 residues). We define three metrics (RMSD threshold for success < 0.4Å):"

  - list:
  - math: E r ( x )
  - math: E r ( x ) = E x 1 ∼ p data R ∼ Unif ( SO ( 3 ) ) [ RMSD ( x ^ ( x 1 ) , R x ^ ( R ⊤ x 1 ) ) ]
  - math: E u ( x )
  - math: U
  - math: E u ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , U x ^ ( R ⊤ x 1 ) ) ]
  - math: E ( x )
  - math: E ( x ) x 1 ∼ p data = E [ RMSD ( x ^ ( x 1 ) , x ^ ( R ⊤ x 1 ) ) ]
  - table:
  - rowgroup:
  - row "Model (Pass Rate) (Pass Rate) (Pass Rate)":
  - columnheader "Model" [ref=e478] [nth=6]
  - columnheader "(Pass Rate)" [ref=e479] [nth=9]:
  - math: E r
  - columnheader "(Pass Rate)" [ref=e480] [nth=10]:
  - math: E u
  - columnheader "(Pass Rate)" [ref=e481] [nth=11]:
  - math: E
  - rowgroup:
  - row "ESM3 VQ-VAE 0% 100% 100%":
  - cell "ESM3 VQ-VAE" [ref=e482] [nth=4]:
  - strong: ESM3 VQ-VAE
  - cell "0%" [ref=e483] [nth=6]
  - cell "100%" [ref=e484] [nth=12]
  - cell "100%" [ref=e485] [nth=13]
  - row "ProteinAE 100% 100% 0%":
  - cell "ProteinAE" [ref=e486] [nth=4]:
  - strong: ProteinAE
  - cell "100%" [ref=e487] [nth=14]
  - cell "100%" [ref=e488] [nth=15]
  - cell "0%" [ref=e489] [nth=7]

  **Analysis:**

  - math: E
  - math: E r
  - strong: invariant
  - math: E r
  - math: E
  - strong: equivariant
  - math: E u

  **2. Geometric Validity Check:**

  - code: stereo_chemical_props.txt
  - table:
  - rowgroup:
  - row "Parameter Atoms Min Max":
  - columnheader "Parameter" [ref=e490] [nth=2]
  - columnheader "Atoms" [ref=e491] [nth=2]
  - columnheader "Min" [ref=e492] [nth=2]
  - columnheader "Max" [ref=e493] [nth=2]
  - rowgroup:
  - row "Backbone - -180 180":
  - cell "Backbone" [ref=e494] [nth=2]:
  - strong:
  - math: ϕ , ψ
  - cell "-" [ref=e495] [nth=4]
  - cell "-180" [ref=e496] [nth=2]
  - cell "180" [ref=e497] [nth=2]
  - row "Bond Length (Å) N - CA 1.399 1.519":
  - cell "Bond Length (Å)" [ref=e498] [nth=2]:
  - strong: Bond Length (Å)
  - cell "N - CA" [ref=e499] [nth=2]
  - cell "1.399" [ref=e500] [nth=2]
  - cell "1.519" [ref=e501] [nth=2]
  - row "CA - C 1.447 1.603":
  - cell
  - cell "CA - C" [ref=e502] [nth=2]
  - cell "1.447" [ref=e503] [nth=2]
  - cell "1.603" [ref=e504] [nth=2]
  - row "C - N 1.280 1.380":
  - cell
  - cell "C - N" [ref=e505] [nth=2]
  - cell "1.280" [ref=e506] [nth=2]
  - cell "1.380" [ref=e507] [nth=2]
  - row "C - O 1.172 1.286":
  - cell
  - cell "C - O" [ref=e508] [nth=2]
  - cell "1.172" [ref=e509] [nth=2]
  - cell "1.286" [ref=e510] [nth=2]
  - row "Bond Angle (°) N - CA - C 102.9 119.1":
  - cell "Bond Angle (°)" [ref=e511] [nth=2]:
  - strong: Bond Angle (°)
  - cell "N - CA - C" [ref=e512] [nth=2]
  - cell "102.9" [ref=e513] [nth=2]
  - cell "119.1" [ref=e514] [nth=2]
  - row "CA - C - N 113.7 126.3":
  - cell
  - cell "CA - C - N" [ref=e515] [nth=2]
  - cell "113.7" [ref=e516] [nth=4]
  - cell "126.3" [ref=e517] [nth=2]
  - row "C - N - CA 113.7 132.3":
  - cell
  - cell "C - N - CA" [ref=e518] [nth=2]
  - cell "113.7" [ref=e519] [nth=5]
  - cell "132.3" [ref=e520] [nth=2]
  - row "CA - C - O 113.8 126.4":
  - cell
  - cell "CA - C - O" [ref=e521] [nth=2]
  - cell "113.8" [ref=e522] [nth=2]
  - cell "126.4" [ref=e523] [nth=2]
  - table:
  - rowgroup:
  - row "Metric Type Violation Ratio (%)":
  - columnheader "Metric" [ref=e524] [nth=2]
  - columnheader "Type" [ref=e525] [nth=3]
  - columnheader "Violation Ratio (%)" [ref=e526] [nth=2]
  - rowgroup:
  - row "Ramachandran 0.00":
  - cell "Ramachandran" [ref=e527] [nth=2]:
  - strong: Ramachandran
  - cell:
  - math: ϕ , ψ
  - cell "0.00" [ref=e528] [nth=6]:

  **0.00**

  - row "Bond Lengths N-CA, CA-C, C-N, C-O 1.24":
  - cell "Bond Lengths" [ref=e529] [nth=2]:
  - strong: Bond Lengths
  - cell "N-CA, CA-C, C-N, C-O" [ref=e530] [nth=2]
  - cell "1.24" [ref=e531] [nth=2]:

  **1.24**

  - row "Bond Angles N-CA-C, CA-C-N, C-N-CA, CA-C-O 1.10":
  - cell "Bond Angles" [ref=e532] [nth=2]:
  - strong: Bond Angles
  - cell "N-CA-C, CA-C-N, C-N-CA, CA-C-O" [ref=e533] [nth=2]
  - cell "1.10" [ref=e534] [nth=2]:

  **1.10**

  - row "Atom Clashes No Overlap 0.00":
  - cell "Atom Clashes" [ref=e535] [nth=2]:
  - strong: Atom Clashes
  - cell "No Overlap" [ref=e536] [nth=2]
  - cell "0.00" [ref=e537] [nth=7]:

  **0.00**

  - row "Left-hand Alpha Helix - 0.00":
  - cell "Left-hand Alpha Helix" [ref=e538] [nth=2]:
  - strong: Left-hand Alpha Helix
  - cell "-" [ref=e539] [nth=5]
  - cell "0.00" [ref=e540] [nth=8]:

  **0.00**

  - emphasis: "Note: Small violation ratios (approx. 1%) are expected as even ground truth structures in AFDB contain minor outliers."
  - button "Public Comment" [ref=e541] [nth=20]
  - group "Collapse controls":
  - button "−" [ref=e542] [nth=20]
  - button "＝" [ref=e543] [nth=20]
  - button "≡" [ref=e544] [nth=20]
  - heading "Replying to Official Comment by Authors" [ref=e545] [nth=5] [level=5]

---

**14. Official Comment by Authors**
- **内容:**

  **Comment:**

  Dear Reviewer qmAJ,
  Thank you again for your constructive feedback.
  "We wanted to confirm that we have updated the manuscript to address your specific points:"

  - list:
  - strong: Included LatentDiff
  - strong: Theoretical Justification

  We believe these additions improve the completeness and presentation of the paper. We would appreciate it if you could take a moment to check these updates.
  Best regards, The Authors

  - button "Public Comment" [ref=e548] [nth=21]
  - contentinfo:
  - list:
  - link "About OpenReview" [ref=e549]:
  - /url: /about
  - link "Hosting a Venue" [ref=e550]:
  - /url: /group?id=OpenReview.net/Support
  - link "All Venues" [ref=e551]:
  - /url: /venues
  - list:
  - link "Contact" [ref=e552]:
  - /url: /contact
  - link "Sponsors" [ref=e553]:
  - /url: /sponsors
  - link "Donate" [ref=e554]:
  - /url: /donate
  - strong: Donate
  - list:
  - link "FAQ" [ref=e555]:
  - /url: https://docs.openreview.net/getting-started/frequently-asked-questions
  - link "Terms of Use" [ref=e556]:
  - /url: /legal/terms
  - link "Privacy Policy" [ref=e557]:
  - /url: /legal/privacy
  - link "News" [ref=e558]:
  - /url: /group?id=OpenReview.net/News&referrer=[Homepage](/)
  - link "OpenReview" [ref=e559]:
  - /url: /about
  - link "OpenReview Sponsors" [ref=e560]:
  - /url: /sponsors
  - alert

---


#### 官方评审 (4 条)

**1. Official Review of Submission11944 by Reviewer FiwP**
- **作者:** Reviewer FiwP
- **日期:** 01 Nov 2025, 17:37
- **内容:**

  - link "Revisions" [ref=e59] [nth=4]:
  - /url: /revisions?id=YExOw0oSBV

  **Summary:**


  In this work, the authors propose using a non-equivariant diffusion autoencoder called ProteinAE to encode protein structure by directly mapping backbone coordinates into a continuous latent space. And they show the performance of their model compared to recent generative frameworks along with its performance as a structure embedder for a downstream prediction task. Overall, the field has largely treated equivariance as gospel—driven by the desire to model structure from first principles and inspired by the success of AlphaFold2. However, AlphaFold3 recently shifted this paradigm. This work presents an interesting application of non-equivariant modeling for generative purposes, while also offering a fast structural encoder, though it still requires further validation and benchmarking to fully establish its advantages.

  **Soundness:**


  **Presentation:**


  **Contribution:**


  **Strengths:**


  - list:

  **Weaknesses:**

  - list:

  **Questions:**

  - list:

  **Flag For Ethics Review:**


  **Rating:**


  **Confidence:**


  **Code Of Conduct:**

  - button "Public Comment" [ref=e60] [nth=4]
  - group "Collapse controls":
  - button "−" [ref=e61] [nth=4]
  - button "＝" [ref=e62] [nth=4]
  - button "≡" [ref=e63] [nth=4]

---

**2. Official Review of Submission11944 by Reviewer MnGk**
- **作者:** Reviewer MnGk
- **日期:** 30 Oct 2025, 12:34
- **内容:**

  - link "Revisions" [ref=e223] [nth=8]:
  - /url: /revisions?id=inwxfx0YW8

  **Summary:**


  This paper proposes PROTEINAE, a protein diffusion autoencoder mapping protein backbone coordinates from E(3) into a continuous, compact latent space for protein modeling and generation. PROTEINAE uses a non-equivariant Diffusion Transformer and is trained with a single flow matching objective to simplify the training objective. PROTEINAE achieves better reconstruction quality and high-quality structure generation that significantly outperforms prior latent-based methods.

  **Soundness:**


  **Presentation:**


  **Contribution:**


  **Strengths:**


  - list:

  **Weaknesses:**

  - list:

  "[1] Geffner, Tomas, et al. \"Proteina: Scaling flow-based protein structure generative models.\" arXiv preprint arXiv:2503.00710 (2025) [2] Geffner, Tomas, et al. \"La-proteina: Atomistic protein generation via partially latent flow matching.\" arXiv preprint arXiv:2507.09466 (2025)."

  **Questions:**

  Please refer to the weakness section

  **Flag For Ethics Review:**


  **Rating:**


  **Confidence:**


  **Code Of Conduct:**


  - button "Public Comment" [ref=e224] [nth=9]
  - group "Collapse controls":
  - button "−" [ref=e225] [nth=9]
  - button "＝" [ref=e226] [nth=9]
  - button "≡" [ref=e227] [nth=9]

---

**3. Official Review of Submission11944 by Reviewer dnyu**
- **作者:** Reviewer dnyu
- **日期:** 29 Oct 2025, 13:14
- **内容:**

  - link "Revisions" [ref=e353] [nth=11]:
  - /url: /revisions?id=KlhJ79VGN7

  **Summary:**


  This paper proposes a new generative model for protein tertiary structure generation and reconstruction. Most existing approaches rely on coordinate prediction models or diffusion models based on stochastic noise denoising, which are computationally expensive and often struggle to maintain structural consistency and reconstruction accuracy. In contrast, this study combines the Flow Matching framework with a Transformer-based network, achieving continuous and stable structure generation. Unlike conventional SE(3)-equivariant models, the proposed method intentionally adopts a non-equivariant architecture on E(3) space. This design eliminates the need for explicit and computationally costly handling of rotations and translations, while still maintaining effective geometric robustness through structure alignment, pairwise bias based on relative distances and angles, and data augmentation.
  The proposed framework consists of three stages. In the first stage, the model takes the backbone atoms of each residue as input and compresses them into residue-level representations using an All-Atom Attention Encoder, which is designed to capture both spatial dependencies among residue pairs and primary sequence information. In the second stage, these features are processed by an Encoder–Decoder structure based on a Diffusion Transformer (DiT), which learns the global 3D correlations of the entire protein. Pairwise representations are incorporated as attention biases, enabling the model to encode global dependencies that reflect inter-residue distances and angles. The third stage introduces the Protein Latent Diffusion Model (PLDM), which treats the latent representations of residue sequences obtained by the encoder as latent token sequences. After compressing both the sequence length and feature dimension, PLDM learns the diffusion process directly in the latent space. Rather than performing stochastic noise denoising, PLDM is designed as a Transformer that predicts the velocity field of latent vectors based on Flow Matching. To preserve the sequential order while integrating temporal embeddings, positional encodings are applied to the latent tokens.
  Experimental evaluation on protein structures from the AlphaFold Database demonstrates that the proposed method achieves smoother and more stable structure generation than conventional diffusion models, with higher reconstruction accuracy as measured by RMSD and FAPE. The generated structures also preserve physical consistency, confirming that the proposed approach enables efficient and high-precision protein structure generation.

  **Soundness:**


  **Presentation:**


  **Contribution:**


  **Strengths:**

  The main strength of this paper lies in its novel design choice to intentionally train the model in a non-equivariant manner on E(3) space, rather than relying on conventional SE(3)-equivariant frameworks. By doing so, the authors successfully avoid the computational cost of explicit rotation and translation handling while maintaining effective geometric robustness through structure alignment, pairwise bias based on relative distances and angles, and appropriate data augmentation. This represents a meaningful and practical contribution to the field of protein structure generation.
  Another notable strength is the use of a simple Flow Matching loss, which removes the need for complex KL or reconstruction losses commonly required in traditional diffusion models. This design enables a smoother and more stable generation process, allowing structures to evolve naturally from noise with higher accuracy and computational efficiency than probabilistic baselines. By integrating Flow Matching with a Transformer architecture, the paper reformulates protein structure generation as learning a continuous flow rather than stochastic denoising, effectively preserving structural continuity and physical consistency while enabling efficient generation in the latent space.

  **Weaknesses:**

  The authors clearly state this limitation, but the proposed model still has difficulty handling very large proteins and multi-chain complexes. Although using a non-equivariant design on E(3) makes the computation much faster, it also creates concerns about whether the model can keep geometric consistency and produce physically reliable results, especially for rotation and translation. Because of this, the method may not yet be suitable for very large or complex protein structures. As the authors mention, adding more geometric constraints or partially equivariant mechanisms in the future could help overcome this problem and further improve the model’s applicability.

  **Questions:**

  Do the authors have any ideas or future plans for incorporating additional constraints or introducing some form of equivariant mechanism to extend the applicability of the proposed model to larger and more complex protein structures?

  **Flag For Ethics Review:**


  **Rating:**


  **Confidence:**


  **Code Of Conduct:**


  - button "Public Comment" [ref=e354] [nth=13]
  - group "Collapse controls":
  - button "−" [ref=e355] [nth=13]
  - button "＝" [ref=e356] [nth=13]
  - button "≡" [ref=e357] [nth=13]

---

**4. Official Review of Submission11944 by Reviewer qmAJ**
- **作者:** Reviewer qmAJ
- **日期:** 27 Oct 2025, 04:47
- **内容:**

  - link "Revisions" [ref=e445] [nth=13]:
  - /url: /revisions?id=Flv2PTwJUR

  **Summary:**


  Unlike prior approaches that depend on SE(3)-equivariant models, discrete tokenization, or multiple loss functions, PROTEINAE simplifies training with a single flow-matching objective and a non-equivariant Diffusion Transformer (DiT) architecture. The model efficiently encodes protein backbones into a latent space through a bottleneck design, enabling high-fidelity reconstruction and scalable downstream modeling. On benchmarks such as CASP14 and CASP15, PROTEINAE achieves state-of-the-art reconstruction accuracy, substantially outperforming discrete and equivariant autoencoders.
  The authors argue that strict equivariance may not be essential for effective protein representation learning, citing recent advances such as AlphaFold3 and Proteina, which also employ non-equivariant architectures. However, the paper could benefit from a more comprehensive discussion of related work on 3D protein autoencoder design, as well as a deeper theoretical justification for the choice of a non-equivariant model.

  **Soundness:**


  **Presentation:**


  **Contribution:**


  **Strengths:**


  - heading "Strengths" [ref=e446] [level=2]
  - list:

  This paper introduces a non-equivariant diffusion autoencoder that learns continuous protein structure representations directly from 3D coordinates, simplifying model design and training compared to SE(3)-equivariant or discrete approaches. But as mentioned before, the paper could benefit from a deeper theoretical justification for the choice of a non-equivariant model.
  The proposed method achieves state-of-the-art reconstruction accuracy on CASP14/15 and competitive structure generation quality relative to more complex diffusion models.
  "Computational efficiency: The latent diffusion framework offers good speed and memory advantages over previous diffusion methods."

  **Weaknesses:**


  - heading "Weaknesses:" [ref=e447] [level=2]
  - list:

  This paper lacks sufficient discussion of prior work on 3D protein backbone structure autoencoder design. For example, the model LatentDiff is compared in Table 2, but it is not discussed in the related-work section. It shares similar design ideas with the proposed method, including an autoencoder that reduces the latent diffusion modelling burden, shrinks the modelling space in terms of length, and offers computational efficiency.
  The authors argue that strict equivariance may not be essential for effective protein representation learning by citing recent advances such as AlphaFold3 and Proteina, which also employ non-equivariant architectures. However, the paper would benefit from a deeper theoretical justification for choosing a non-equivariant model.

  **Questions:**

  As listed above in weaknesses.

  **Flag For Ethics Review:**


  **Rating:**


  **Confidence:**


  **Code Of Conduct:**


  - button "Public Comment" [ref=e448] [nth=17]
  - group "Collapse controls":
  - button "−" [ref=e449] [nth=17]
  - button "＝" [ref=e450] [nth=17]
  - button "≡" [ref=e451] [nth=17]

---


#### 修订总结 (1 条)

**1. Summary of Revisions and Response to Reviewers**
- **作者:** Authors
- **日期:** 30 Nov 2025, 00:58
- **内容:**

  - strong: Summary of Revisions and Response to Reviewers
  - link "Revisions" [ref=e52] [nth=3]:
  - /url: /revisions?id=CXsGhQJcox

  **Comment:**


  We would like to thank you and the reviewers for the time and effort dedicated to reviewing our work. The constructive feedback has helped us significantly improve the quality and completeness of our manuscript.
  "We have actively engaged with all reviewers and provided a comprehensive revision. Below is a summary of the key updates addressing the reviewers' main concerns:"

  - strong: 1. Expanded Benchmarks & Baselines (Addressing Reviewers FiwP & MnGk)
  - list:

  **New Baselines:**

  - strong: Proteina

  **CAMEO Benchmark:**

  - strong: CAMEO
  - strong: 2. Enhanced Generative Performance & Designability (Addressing Reviewers MnGk & FiwP)
  - list:

  **Improved Generation Quality:**

  - strong: implementing a time-shifting technique
  - strong: scaling up the model channel dimensions
  - strong: 3. Equivariance, Validity & Related Work (Addressing Reviewers FiwP, MnGk & qmAJ)
  - list:

  **SE(3) & Physical Consistency:**

  - strong: Flow Matching

  **Related Work:**

  - strong: LatentDiff
  - strong: 4. Downstream Utility (Addressing Reviewer FiwP)
  - list:
  - strong: Bind, Cat and Con
  - strong: 5. Perspective of ProteinAE v2 (Addressing Reviewer dnyu)
  - list:

  **Future Roadmap & Multi-Modal Support:**

  - strong: ProteinAE v2
  - strong: preliminary visualization results in Appendix Fig. 5
  - strong: Conclusion
  - strong: dnyu
  - strong: qmAJ
  - strong: FiwP
  - strong: MnGk

  We remain available for any further questions.
  Best regards,
  The Authors

  - button "Public Comment" [ref=e53] [nth=3]
  - group "Collapse controls":
  - button "−" [ref=e54] [nth=3]
  - button "＝" [ref=e55] [nth=3]
  - button "≡" [ref=e56] [nth=3]

---

