# RSLiveBench-UAV

**A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence**

[Project website](https://rslivebench.space/) · [Dataset on Hugging Face](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV)

RSLiveBench-UAV evaluates how vision-language models understand vehicles, scenes, and spatial relationships in UAV imagery. The project covers object recognition, 2D and 3D perception, cross-view correspondence, and reasoning.

## Minival-928 release

The human-verified Minival-928 release provides a compact offline evaluation set. It is distinct from the larger Start-10 benchmark.

| Item | Minival-928 |
| --- | ---: |
| Questions | 928 |
| Unique anonymized images | 597 |
| Task types | 17 |
| Evaluation groups | 4 |
| Included reference model runs | 16 |

The [Hugging Face dataset repository](https://huggingface.co/datasets/erenzhou/RSLiveBench-UAV) is the destination for the release package, including English prompts, anonymized images, gold answers, evaluation scripts, and reference predictions. Check that page for the current file availability before downloading.

## What the benchmark measures

| Group | Tasks |
| --- | --- |
| **2D perception** | Brand and model recognition, single-image counting, spatial relations, weather, and vehicle heading. |
| **3D perception** | Vehicle dimensions and relative or absolute distance. |
| **Cross-view perception** | Counting, grounding, and instance re-identification across views. |
| **Reasoning** | Camera height and pitch, vehicle polar coordinates, capture location, and capture hour. |

Questions refer to one or two images. For two-image questions, keep the image order specified in each question record. Prompts define the required answer format; visual-grounding boxes use coordinates normalized to `[0,1000]` by default.

## Evaluate a model

After downloading the Minival-928 package from Hugging Face, create a JSONL file with **one string answer for each question ID**:

```json
{"question_id":"suite::hd002-distance_extreme-00636","answer":"[645,528,754,614]"}
```

From the root of the downloaded dataset package, run:

```bash
python evaluator/score_all.py --predictions your_predictions.jsonl --output score_output
```

The evaluator requires Python 3.10+ and only the standard library. It reports scores for all 17 tasks, the four evaluation groups, and an overall score. **Overall is the equal-weight mean of the four group scores**, rather than a direct average of questions or tasks. The dataset package's evaluation guide documents task-specific metrics and alternate box-coordinate modes.

The package also includes predictions from 16 reference models and a script to reproduce their reported scores:

```bash
python reference_predictions/evaluate_all.py --output reproduced_scores
```

## Privacy and responsible use

The release images use anonymized filenames and have capture metadata removed. Confirmed license-plate regions were blurred. An automatic non-detection is not a guarantee that an image contains no visible plate. Gold answers and reference predictions are included for reproducibility; using them for training or prompt tuning can compromise future evaluation results.

## License

The **Minival-928 dataset** is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). Reuse requires appropriate credit, a link to the license, and an indication of changes.

## Citation

If you use the benchmark, cite *RSLiveBench-UAV: A Continually Evolving Vision-Language Benchmark for Aerial Spatial Intelligence*. An official citation entry has not yet been provided.
