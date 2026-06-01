# LL-Bench: Rethinking Low-Level Vision Evaluation in the Era of Large-Scale Generative Models via Human Preferences

This is the official implementation of LL-Bench. The full dataset and code will be released upon publication. 

<p align="center">
  <img src="assets/llbench.png" width="95%" alt="LL-Bench overview">
</p>

## 📦 LL-Bench Dataset

**LL-Bench** is a large-scale human-preference benchmark for low-level vision evaluation. It covers 16 low-level vision tasks.


**Image Asset**:
- <u><i>28,919</i></u> restored images (16 tasks)
- <u><i>2,469</i></u> real-world degraded source images  (16 tasks)

**Human Preference Asset**:
- <u><i>152,020</i></u> pairwise preference annotations
- <u><i>28,334</i></u> Bradley-Terry quality scores
- <u><i>28,919</i></u> hallucination labels

**Examples**:

<!-- <p align="center"><b>Super Resolution</b></p>

<p align="center">
  <img src="assets/examples/super_resolution_lr60_012.png" width="95%" alt="LL-Bench super resolution example">
</p> -->

<p align="left"><b>Removal: Raindrop Removal</b></p>

<p align="center">
  <img src="assets/examples/raindrop_rainDrop23.png" width="95%" alt="LL-Bench raindrop removal example">
</p>

<p align="left"><b>Enhancement: HDR Imaging</b></p>

<p align="center">
  <img src="assets/examples/hdr_imaging_hdrplus_0234.png" width="95%" alt="LL-Bench HDR imaging example">
</p>

<p align="left"><b>Restoration: Old Photo Restoration</b></p>

<p align="center">
  <img src="assets/examples/old_photo_uncompleted_inpnt13.png" width="95%" alt="LL-Bench old photo restoration example">
</p>


## 🧭 LL-Score

**LL-Score** is a Qwen3-VL based evaluator for low-level vision. Given a degraded
image, a restored image, and the task name, LL-Score internally wraps the task
into the evaluation instruction and jointly predicts:

- a human-preference-aligned quality score;
- a hallucination probability.


<p align="center">
  <img src="assets/ll_score_method.png" width="90%" alt="LL-Score method">
</p>



## ✅ To Do

-  Dataset
-  Inference Code
-  Training Code and others: release upon publication
