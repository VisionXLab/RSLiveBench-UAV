<div align="center">

# RSLiveBench-UAV

### A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence

<p>
  Yue Zhou<sup>1</sup>, Jiawei Liu<sup>1</sup>, Jue Chen<sup>1</sup>,
  Ziyang Gong<sup>2</sup>, Haojia Wei<sup>4</sup>, Jingxiang Li<sup>5</sup><br>
  Xue Jiang<sup>2</sup>, Zhihang Zhong<sup>2</sup>, Pai Peng<sup>3</sup>,
  Xue Yang<sup>2,3,*</sup>, Yansheng Li<sup>6</sup>, Jonathan Li<sup>5,*</sup>
</p>

<p>
  <sup>1</sup>East China Normal University &nbsp;·&nbsp;
  <sup>2</sup>Shanghai Jiao Tong University &nbsp;·&nbsp;
  <sup>3</sup>Cowarobot<br>
  <sup>4</sup>University of California, Los Angeles &nbsp;·&nbsp;
  <sup>5</sup>University of Waterloo &nbsp;·&nbsp;
  <sup>6</sup>Wuhan University<br>
  <sup>*</sup>Corresponding authors
</p>

<p>
  <a href="https://rslivebench.space/"><img src="https://img.shields.io/badge/Project-Website-2563EB?style=flat-square" alt="Project website"></a>
  <a href="https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV"><img src="https://img.shields.io/badge/Hugging%20Face-Dataset-FFD21E?style=flat-square&logo=huggingface&logoColor=black" alt="Hugging Face dataset"></a>
  <a href="https://creativecommons.org/licenses/by/4.0/"><img src="https://img.shields.io/badge/License-CC%20BY%204.0-16A34A?style=flat-square" alt="CC BY 4.0 license"></a>
</p>

<p><strong>Core production by
  <a href="http://zhouyue.space/">DREAMS@ECNU</a> ·
  <a href="https://yangxue.site/">VisionXLab@SJTU</a> ·
  <a href="https://www.cowarobot.com/home">Cowarobot</a>
</strong></p>

**Public validation: 928 questions · Server-scored test: 35,491 questions · 17 tasks**

[Overview](#-overview) · [Benchmark](#-benchmark-at-a-glance) · [Results](#-minival-928-results) · [Dataset](#-dataset) · [Evaluation](#-evaluation) · [Citation](#-citation)

</div>

## 📖 Overview

RSLiveBench-UAV evaluates how vision-language models understand vehicles, scenes, and spatial relationships in UAV imagery. It spans recognition, 2D and 3D perception, cross-view correspondence, and reasoning.

The benchmark has two evaluation splits:

| Split | Role | Scoring |
| :--- | :--- | :--- |
| **Minival-928 · public validation** | 928 human-verified questions selected from Full for development and reproducible comparisons | Gold answers and a local evaluator are included. |
| **Start-10 Full · server-scored test** | 35,491 human-verified questions across ten aerial scenes | All 35,491 questions contribute to the official score; server-side scoring will open at [rslivebench.space](https://rslivebench.space/). |

Both splits are hosted in the [Hugging Face dataset](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV). Submit predictions for all Full questions; its official score covers **all 35,491 questions**, including the **928 shared with Minival-928**. Those 928 answers are already available in Minival-928; the other 34,563 answers remain server-side.

Minival-928 balances all 17 task types and was selected to closely preserve model rankings relative to Full. The gold answers for both splits have been human-verified.

Starting in **December 2026**, we will release a new benchmark pair every month: a smaller **public validation set** with answers and a larger **private test set** whose answers remain on the scoring server.

## ✨ Highlights

- **Aerial spatial understanding:** evaluate fine-grained vehicle attributes, geometry, and relationships from UAV views.
- **Single- and cross-view questions:** test both image-level perception and correspondence across two views.
- **Reproducible scoring:** use the included evaluator for task, group, and overall scores.
- **Reference runs:** compare against predictions from 16 included model runs.
- **Privacy-conscious release:** images have anonymized filenames, removed capture metadata, and blurred confirmed license-plate regions.

## 📊 Benchmark at a glance

| Minival-928 | Count |
| :--- | ---: |
| Questions | **928** |
| Unique anonymized images | **597** |
| Task types | **17** |
| Evaluation groups | **4** |
| Bundled reference model runs | **16** |
| Models in results table | **30** |

### Task groups

| Group | What it measures |
| :--- | :--- |
| **2D perception** | Brand and model recognition, single-image counting, spatial relations, weather, and vehicle heading. |
| **3D perception** | Vehicle dimensions and relative or absolute distance. |
| **Cross-view perception** | Counting, grounding, and instance re-identification across views. |
| **Reasoning** | Camera height and pitch, vehicle polar coordinates, capture location, and capture hour. |

## 🔥 Minival-928 results

All 30 models have predictions for the same 928 questions. The 16 **Bundled** runs are included in the [Hugging Face dataset](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV/tree/main/reference_predictions). The 14 **Rescored** runs were extracted from archived full-benchmark predictions and evaluated with the same Minival-928 release evaluator and gold answers. Their per-question predictions are not currently included in the Hugging Face package.

Scores are percentages (higher is better). **Overall** is the equal-weight mean of the four evaluation groups. Bold marks the highest score in each column. [Download exact scores as CSV](minival_928_30_models.csv).

| Model | 2D perception | 3D perception | Cross-view perception | Reasoning | Overall |
| :--- | ---: | ---: | ---: | ---: | ---: |
| gpt-6-astra / low | 60.15 | **83.11** | **85.95** | **41.49** | **67.67** |
| gpt-6.1-sol / low | **62.90** | 79.89 | 82.72 | 40.00 | 66.38 |
| ACE-Brain-0.6-9B | 40.69 | 72.69 | 58.37 | 15.00 | 46.69 |
| gpt-5.6-luna / low | 41.34 | 64.30 | 44.63 | 23.33 | 43.40 |
| DeepSeek-V4.1-Flash-1017 / low | 45.05 | 62.76 | 33.76 | 19.97 | 40.39 |
| RynnBrain1.1-9B | 38.18 | 59.35 | 46.20 | 15.62 | 39.84 |
| Qwen3.5-9B | 46.15 | 71.03 | 20.22 | 20.43 | 39.46 |
| RoboBrain2.5-8B-NV | 40.26 | 58.63 | 17.44 | 23.58 | 34.98 |
| Qwen3-VL-8B-Instruct | 47.03 | 50.26 | 21.41 | 21.12 | 34.96 |
| RynnBrain-8B | 36.66 | 50.22 | 21.81 | 26.39 | 33.77 |
| PhysBrain1.5-8B | 29.50 | 34.58 | 23.08 | 16.92 | 26.02 |
| MiMo-Embodied-7B | 27.79 | 40.96 | 13.87 | 19.32 | 25.48 |
| Cosmos-Reason2-8B | 31.16 | 20.02 | 17.16 | 25.44 | 23.45 |
| ACE-Brain-0-8B | 23.07 | 35.00 | 14.19 | 19.40 | 22.91 |
| SenseNova-SI-1.4-InternVL3-8B | 27.03 | 12.68 | 24.35 | 21.36 | 21.35 |
| InternVL3.5-4B | 25.48 | 26.92 | 15.52 | 15.19 | 20.78 |
| SenseNova-SI-1.3-InternVL3-8B | 25.23 | 15.79 | 17.82 | 17.32 | 19.04 |
| InternVL3.5-8B | 29.11 | 19.88 | 17.45 | 9.62 | 19.02 |
| SenseNova-SI-1.5-InternVL3-8B | 26.73 | 11.01 | 22.91 | 13.58 | 18.56 |
| SenseNova-SI-1.1-InternVL3-8B | 33.08 | 8.17 | 15.44 | 15.69 | 18.10 |
| ACE-Brain-0.5-8B | 29.14 | 9.63 | 14.54 | 14.07 | 16.84 |
| Qwen3.5-2B | 38.05 | 15.93 | 5.58 | 7.58 | 16.79 |
| RynnBrain-2B | 32.03 | 9.30 | 13.15 | 8.75 | 15.81 |
| RynnBrain1.1-2B | 22.93 | 9.17 | 20.67 | 9.54 | 15.58 |
| Cosmos-Reason2-2B | 28.65 | 9.01 | 14.54 | 8.29 | 15.12 |
| Pelican1.0-VL-7B (2K) | 26.03 | 2.12 | 14.22 | 15.53 | 14.48 |
| SenseNova-SI-1.1-InternVL3-2B | 23.56 | 2.54 | 14.76 | 5.69 | 11.64 |
| GeoChat-7B | 12.19 | 6.88 | 7.64 | 10.93 | 9.41 |
| VHM | 10.42 | 0.33 | 7.96 | 0.97 | 4.92 |
| GeoLLaVA-8K | 0.83 | 0.00 | 0.00 | 0.00 | 0.21 |

The 16 bundled runs were re-evaluated and their reports matched the shipped `reference_report.json` files exactly. All 14 additional runs passed the 928-question coverage check. Visual-grounding coordinates use each model's recorded protocol; the new runs use `[0, 1000]`. Audited output-format conversions were applied to RynnBrain and SenseNova predictions before scoring.
## 📦 Dataset

The [Hugging Face dataset repository](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV) contains both splits. Minival-928 includes English prompts, anonymized images, gold answers, an evaluator, and reference predictions. [Start-10 Full](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV/tree/main/start10_full) provides prompts, anonymized images, and a prediction template; its complete answer key and scoring service are held on the benchmark server. Minival-928 reveals the answers to the 928 shared Full questions.

Questions refer to one or two images. For two-image questions, preserve the image order in the question record. Each prompt specifies its answer format; visual-grounding boxes use coordinates normalized to `[0, 1000]` by default.

## 🚀 Evaluation

### 1. Prepare predictions

After obtaining the dataset package, write one string answer per question ID to a JSONL file:

```json
{"question_id":"suite::hd002-distance_extreme-00636","answer":"[645,528,754,614]"}
```

### 2. Score your model

For the Minival-928 public validation split, run from the root of the downloaded dataset package:

```bash
python evaluator/score_all.py --predictions your_predictions.jsonl --output score_output
```

The evaluator requires Python 3.10+ and uses only the standard library. It reports scores for all 17 tasks, each of the four groups, and an overall score. **The overall score is the equal-weight mean of the four group scores.** See the evaluation guide in the dataset package for task-specific metrics and alternate box-coordinate modes.

### 3. Reproduce reference scores

The package includes predictions from 16 reference model runs:

```bash
python reference_predictions/evaluate_all.py --output reproduced_scores
```

For the Start-10 Full server-scored test split, prepare a prediction for every question using its template and submit to [rslivebench.space](https://rslivebench.space/) when the Full submission route opens. Its official score is computed on all 35,491 questions, including the Minival-928 overlap.

## 🔒 Privacy and responsible use

Confirmed license-plate regions were blurred, but an automatic non-detection does not guarantee that no visible plate remains. Gold answers and reference predictions are provided for reproducibility; using them for training or prompt tuning can compromise future evaluation results.

## 📄 License

The **Minival-928 dataset** is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Reuse requires appropriate credit, a link to the license, and an indication of changes.

## 📝 Citation

If you use this benchmark, please cite *RSLiveBench-UAV: A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence*. An official citation entry has not yet been provided.
