# CV, NLP, and multimodal review rubric

Use this as a review checklist, not a scorecard. Apply only relevant checks.

## Universal checks

- Separate empirical improvement from causal or general-capability claims.
- Check baseline parity, leakage, splits, uncertainty, ablations, and fair compute/data/inference comparisons.
- Test whether conclusions exceed their supporting experiments, theorems, or analyses.

## Computer vision

- Verify source, annotation, split, preprocessing, augmentation, resolution, and protocol consistency.
- For robustness/generalization, check shifts, calibration, subgroup behavior, and failures—not one aggregate metric.
- For generative work, distinguish perceptual quality from faithfulness and inspect selection bias.
- For vision-language work, check modality contribution, prompt sensitivity, frozen/trained components, and data overlap.

## NLP and language models

- Verify train/dev/test separation, deduplication, contamination, licensing, PII handling, language and domain coverage.
- Separate capability from prompting, retrieval, tools, agent scaffolding, and post-processing.
- Check prompt variance, evaluator choice, human-evaluation design, and multilingual validity.
- For safety/bias claims, check threat model, coverage, error trade-offs, and deployment harm.

## Theory, methods, and benchmarks

- Match theorem statements to assumptions and practical relevance.
- For benchmarks, assess construct validity, annotation quality, leakage controls, metric incentives, and contamination resistance.
- For methods, identify exact novelty, complexity, hyperparameter sensitivity, and failure conditions.
