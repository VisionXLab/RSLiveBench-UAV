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

**928 questions · 597 UAV images · 17 tasks · 4 evaluation groups**

[Overview](#-overview) · [Benchmark](#-benchmark-at-a-glance) · [Results](#-minival-928-results) · [Dataset](#-dataset) · [Evaluation](#-evaluation) · [Citation](#-citation)

</div>

## 📖 Overview

RSLiveBench-UAV evaluates how vision-language models understand vehicles, scenes, and spatial relationships in UAV imagery. It spans recognition, 2D and 3D perception, cross-view correspondence, and reasoning.

**Minival-928** is a human-verified, compact offline evaluation release. It is distinct from the larger Start-10 benchmark. The dataset, gold answers, evaluator, and reference predictions are hosted on [Hugging Face](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV).

> [!NOTE]
> The GitHub and Hugging Face repositories are currently private. Access requires authorization from the repository owners.

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
| Reference model runs | **16** |

### Task groups

| Group | What it measures |
| :--- | :--- |
| **2D perception** | Brand and model recognition, single-image counting, spatial relations, weather, and vehicle heading. |
| **3D perception** | Vehicle dimensions and relative or absolute distance. |
| **Cross-view perception** | Counting, grounding, and instance re-identification across views. |
| **Reasoning** | Camera height and pitch, vehicle polar coordinates, capture location, and capture hour. |

## 🔥 Minival-928 results

The table reports scores from the 16 bundled reference model runs. Every model has predictions for all 928 questions. Scores range from 0 to 100, and higher is better. Models are ranked by **Overall**, the equal-weight mean of the four evaluation groups. **Bold** marks the best score in each column.

| Rank | Model | 2D perception | 3D perception | Cross-view perception | Reasoning | Overall |
| ---: | :--- | ---: | ---: | ---: | ---: | ---: |
| 1 | gpt-6.1-sol / low | **62.90** | **79.89** | **82.72** | **40.00** | **66.38** |
| 2 | ACE-Brain-0.6-9B | 40.69 | 72.69 | 58.37 | 15.00 | 46.69 |
| 3 | gpt-5.6-luna / low | 41.34 | 64.30 | 44.63 | 23.33 | 43.40 |
| 4 | DeepSeek-V4.1-Flash-1017 / low | 45.05 | 62.76 | 33.76 | 19.97 | 40.39 |
| 5 | Qwen3.5-9B | 46.15 | 71.03 | 20.22 | 20.43 | 39.46 |
| 6 | RoboBrain2.5-8B-NV | 40.26 | 58.63 | 17.44 | 23.58 | 34.98 |
| 7 | Qwen3-VL-8B-Instruct | 47.03 | 50.26 | 21.41 | 21.12 | 34.96 |
| 8 | PhysBrain1.5-8B | 29.50 | 34.58 | 23.08 | 16.92 | 26.02 |
| 9 | MiMo-Embodied-7B | 27.79 | 40.96 | 13.87 | 19.32 | 25.48 |
| 10 | ACE-Brain-0-8B | 23.07 | 35.00 | 14.19 | 19.40 | 22.91 |
| 11 | InternVL3.5-4B | 25.48 | 26.92 | 15.52 | 15.19 | 20.78 |
| 12 | InternVL3.5-8B | 29.11 | 19.88 | 17.45 | 9.62 | 19.02 |
| 13 | Qwen3.5-2B | 38.05 | 15.93 | 5.58 | 7.58 | 16.79 |
| 14 | GeoChat-7B | 12.19 | 6.88 | 7.64 | 10.93 | 9.41 |
| 15 | VHM | 10.42 | 0.33 | 7.96 | 0.97 | 4.92 |
| 16 | GeoLLaVA-8K | 0.83 | 0.00 | 0.00 | 0.00 | 0.21 |

These values come from the `reference_report.json` files in the [Hugging Face `reference_predictions/` directory](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV/tree/main/reference_predictions). Use the reproduction command below to recalculate them with the included evaluator. The bundled model registry records the Visual Grounding coordinate mode used for each run.

## 📦 Dataset

The [Hugging Face dataset repository](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV) contains English prompts, anonymized images, gold answers, evaluation scripts, and reference predictions. Its dataset card provides the release details and file layout.

Questions refer to one or two images. For two-image questions, preserve the image order in the question record. Each prompt specifies its answer format; visual-grounding boxes use coordinates normalized to `[0, 1000]` by default.

## 🚀 Evaluation

### 1. Prepare predictions

After obtaining the dataset package, write one string answer per question ID to a JSONL file:

```json
{"question_id":"suite::hd002-distance_extreme-00636","answer":"[645,528,754,614]"}
```

### 2. Score your model

From the root of the downloaded dataset package, run:

```bash
python evaluator/score_all.py --predictions your_predictions.jsonl --output score_output
```

The evaluator requires Python 3.10+ and uses only the standard library. It reports scores for all 17 tasks, each of the four groups, and an overall score. **The overall score is the equal-weight mean of the four group scores.** See the evaluation guide in the dataset package for task-specific metrics and alternate box-coordinate modes.

### 3. Reproduce reference scores

The package includes predictions from 16 reference model runs:

```bash
python reference_predictions/evaluate_all.py --output reproduced_scores
```

## 🔒 Privacy and responsible use

Confirmed license-plate regions were blurred, but an automatic non-detection does not guarantee that no visible plate remains. Gold answers and reference predictions are provided for reproducibility; using them for training or prompt tuning can compromise future evaluation results.

## 📄 License

The **Minival-928 dataset** is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Reuse requires appropriate credit, a link to the license, and an indication of changes.

## 📝 Citation

If you use this benchmark, please cite *RSLiveBench-UAV: A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence*. An official citation entry has not yet been provided.
