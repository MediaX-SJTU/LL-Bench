# LL-Bench: Rethinking Low-Level Vision Evaluation in the Era of Large-Scale Generative Models via Human Preferences

This is the offical implementation of LL-Bench. 

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

<!-- TODO: add LL-Score method figure
<p align="center">
  <img src="assets/ll_score_method.png" width="90%" alt="LL-Score method">
</p>
-->

### Inference Code

Install dependencies:

```bash
pip install -r requirements.txt
```

Edit `configs/inference.yaml`:

```yaml
model_name_or_path: "/path/to/Qwen3-VL-8B-Instruct"
checkpoint_dir: "/path/to/ll-score-checkpoint"
checkpoint_step: -1
device: "cuda"
batch_size: 1
```

Prepare an input JSONL file. Each line is one candidate restored image:

```json
{"id": "sample_001", "task": "Raindrop Removal", "degraded_image": "/path/to/degraded.png", "restored_image": "/path/to/restored.png"}
```

Run inference:

```bash
python -m ll_score.infer \
  --config configs/inference.yaml \
  --input-jsonl examples/input.jsonl \
  --output-jsonl outputs/predictions.jsonl
```

The output JSONL preserves the input fields and appends:

- `quality_score`
- `hallucination_prob`

## ✅ To Do

-  Dataset
-  Inference Code
-  Training Code and others: release upon publication

## Anonymous Review

This repository is prepared for anonymous review. Author identities,
institutional metadata, and final citation information are intentionally omitted
during the review period.
