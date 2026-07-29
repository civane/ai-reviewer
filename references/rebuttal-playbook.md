# Rebuttal and re-review playbook

Use this as an action library, not a formula for gaming review. An action is persuasive only when it directly changes evidence behind the original concern.

| Failure mode | Minimum convincing action | Weak response to avoid |
| --- | --- | --- |
| Weak/mismatched baseline | Add a matched, tuned baseline or explain an unavoidable mismatch with protocol details | Calling the baseline “standard” without comparison |
| Missing ablation/mechanism | Isolate the component with a controlled ablation and uncertainty | Repeating intuition or examples only |
| Efficiency claim | Report total cost to fixed quality: time, memory, hardware, data, convergence | Per-step time alone |
| Generalization/OOD claim | Add the relevant held-out shift/sensitivity test or narrow the claim | In-distribution metric only |
| Benchmark/evaluator validity | Audit contamination, prompt/evaluator dependence, human validation, data statistics | Treating LLM-judge score as self-validating |
| Theory/proof concern | Point to exact assumption; correct statement; add proof/counterexample | Broad “the theorem still holds” assertion |
| Reproducibility/clarity | Add prompts, seeds, hyperparameters, splits, compute, code path, diagram/table | Promising details later |

For each concern: acknowledge its precise premise; state action; give new evidence and location; say what remains limited. Raise confidence only when the action addresses the original decision-relevant gap.
