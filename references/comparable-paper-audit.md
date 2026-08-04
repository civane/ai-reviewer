# Comparable-paper audit

Use this to decide whether an experiment from prior work is required, useful, or not comparable.

A direct comparator should match task/construct, data distribution and split, output/metric, model or intervention setting, train/test access, and material compute or deployment constraint. A paper can be important context without being a fair baseline.

Check datasets/splits/preprocessing; metrics and uncertainty; baselines, tuning, model/data/compute budgets; ablations; OOD/robustness/scalability/failures; and human or judge protocol where relevant.

- **Missing for fair comparison:** required for a head-to-head, efficiency, generalization, or superiority claim in the same regime.
- **High-value optional evidence:** strengthens confidence but is outside the stated central setting.
- **Not comparable without a new protocol:** task, data, access, metric, or budget mismatch prevents a meaningful numerical conclusion.

Record each conclusion with a source location. Do not infer unreported settings or treat a missing result as a negative result.
