<div align="center">

# RSLiveBench-UAV

### A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence

<p>
  <a href="https://rslivebench.space/"><img src="https://img.shields.io/badge/Project-Website-2563EB?style=flat-square" alt="Project website"></a>
  <a href="https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV"><img src="https://img.shields.io/badge/Hugging%20Face-Dataset-FFD21E?style=flat-square&logo=huggingface&logoColor=black" alt="Hugging Face dataset"></a>
  <a href="https://creativecommons.org/licenses/by/4.0/"><img src="https://img.shields.io/badge/License-CC%20BY%204.0-16A34A?style=flat-square" alt="CC BY 4.0 license"></a>
</p>

**928 questions · 597 UAV images · 17 tasks · 4 evaluation groups**

[Overview](#-overview) · [Benchmark](#-benchmark-at-a-glance) · [Dataset](#-dataset) · [Evaluation](#-evaluation) · [Citation](#-citation)

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
