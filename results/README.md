# Experiment Results

Metrics below were captured from the completed notebook run.

## Clean test-set performance

| Metric | Initial CNN | Adversarially trained CNN |
|---|---:|---:|
| Loss | 0.2597 | 0.2999 |
| Accuracy | 86.33% | 89.92% |
| Weighted precision | 86.34% | 90.00% |
| Weighted recall | 86.33% | 89.92% |
| Weighted F1 | 86.33% | 89.92% |

Test set: 1,280 images (640 per class).

## FGSM accuracy

| Evaluation | Accuracy |
|---|---:|
| Before adversarial training | 11.56% |
| After adversarial training | 89.92% |

FGSM epsilon: 0.1. Adversarial training ratio: 0.5.

## Notes

- These are results from one experimental run, not independently reproduced benchmarks.
- The split was stratified at image level, not patient level. Patient-level separation should be used if patient identifiers are available.
- The identical rounded post-training clean and FGSM accuracies warrant additional evaluation at multiple epsilon values and with stronger attacks.
- These results do not establish clinical diagnostic performance.
