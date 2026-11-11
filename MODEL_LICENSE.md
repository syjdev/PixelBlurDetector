# Model License & Provenance

This document covers the **machine-learning model artifacts** shipped in the PixelBlurDetector
SDKs, which the demo apps in this repository use. They are licensed **separately** from the
source code. Each SDK repository has its own copy of this document.

| Artifact | Shipped in |
|---|---|
| Core ML model (float), `BlurSegmentation.mlpackage` | [PixelBlurDetector-iOS](https://github.com/syjdev/PixelBlurDetector-iOS) |
| TensorFlow Lite model (float), `blur_segmentation_float.tflite` | [PixelBlurDetector-Android](https://github.com/syjdev/PixelBlurDetector-Android) |

> The **source code** is licensed under **Apache-2.0** (see [`LICENSE`](LICENSE)). The Apache-2.0
> license does **not** apply to the model artifacts listed above.

## Training data

The models were trained on three academic datasets:

1. **CUHK Blur Detection Dataset**
   (J. Shi, L. Xu, J. Jia, *"Discriminative Blur Detection Features"*, CVPR 2014)
   <http://www.cse.cuhk.edu.hk/~leojia/projects/dblurdetect/dataset.html>
2. **DUT-DBD Dataset**
   (W. Zhao, F. Zhao, D. Wang, H. Lu, *"Defocus Blur Detection via Multi-stream Bottom-Top-Bottom
   Fully Convolutional Network"*, CVPR 2018)
   <https://openaccess.thecvf.com/content_cvpr_2018/html/Zhao_Defocus_Blur_Detection_CVPR_2018_paper.html>
3. **EBD Dataset**
   (Y. Jin, M. Qian, J. Xiong, N. Xue, G.-S. Xia, *"Depth and DOF Cues Make A Better Defocus Blur
   Detector"*, ICME 2023)
   <https://github.com/yuxinjin-whu/D-DFFNet>

> **Correction (October 2026):** earlier versions of this document listed only CUHK and DUT-DBD.
> The training data also included EBD, which was left out by mistake.

## Current status: license unclear, non-commercial for now ⚠️

**None of the three datasets states a license.** As of October 2026:

- The CUHK dataset page describes the data and links the downloads, but gives no license, terms of
  use or statement about commercial use.
- The original DUT-DBD project page (`ice.dlut.edu.cn/ZhaoWenda/BTBCRLNet.html`) is no longer
  reachable, and no license for the dataset has been found elsewhere.
- The EBD dataset is distributed through the authors' code repository, which describes it as a
  test set and gives no license for the dataset or the code.

Without a license, we can't confirm that commercial use of these datasets, or of models trained on
them, is allowed. Whether trained model weights are a derivative work of their training data is
also legally unsettled. Until this is resolved:

- The model artifacts are offered for **research and non-commercial use only**.
- **Do not ship them in a commercial or closed-source application.**
- If you want to use them commercially, **contact the authors of all three datasets first.**
  Permission for one or two of them is not enough, because the models were trained on all three.

This is a conservative, good-faith position, **not legal advice**.

## Making the models commercially usable

One of the following must happen first:

1. **Get written permission** from the authors of **all three** datasets (CUHK, DUT-DBD and EBD) for
   commercial use of models trained on them, and record it here (and in `NOTICE`).
2. **Retrain** the models on data whose license allows commercial use (or on self-collected data),
   and replace the artifacts above in both SDKs.

Until then, only the **Apache-2.0 source code** can be reused commercially, not the bundled models.

## Demo and test images (CC0) ✅

The repository used to include original **dataset** images (`dut_test_*`, `motion*`,
`out_of_focus*`) as demo assets and test fixtures. Academic datasets generally don't grant
redistribution rights, so those images were **removed** and replaced with **CC0 / public-domain**
images from Wikimedia Commons. CC0 requires no attribution and allows commercial use. See
[Sample image credits](README.md#sample-image-credits) in the README.

The datasets above therefore affect **only the trained model weights**, not the bundled sample
images.

> **Note on git history:** the old dataset images still exist in earlier commits. Removing them
> going forward does not purge them from history. A history rewrite (`git filter-repo` / BFG) is
> needed to remove them completely.
