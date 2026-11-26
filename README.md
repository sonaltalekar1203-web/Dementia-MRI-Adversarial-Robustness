# Dementia MRI Classification & Adversarial Robustness

A PyTorch-based experimental project that classifies brain MRI images into **Dementia** and **No Dementia** categories, then evaluates the effect of FGSM adversarial perturbations and ART adversarial training.

> **Research disclaimer:** This is an educational machine-learning experiment, not a clinically validated diagnostic system. It must not be used to diagnose, screen, or guide treatment.

## Project highlights

- Binary MRI image classification with a custom convolutional neural network (CNN).
- Fast Gradient Sign Method (FGSM) adversarial attack using the Adversarial Robustness Toolbox (ART).
- Adversarial training with a 0.5 adversarial sample ratio.
- Clean and adversarial accuracy comparison.
- t-SNE visualization of learned latent features before and after adversarial training.
- Google Colab execution with GPU acceleration (the recorded run used an NVIDIA Tesla T4).

## Dataset

The experiment used 6,400 preprocessed MRI images in two balanced classes:

| Class | Images |
|---|---:|
| Dementia | 3,200 |
| No Dementia | 3,200 |
| **Total** | **6,400** |

The notebook expects a ZIP file containing folders named `Dementia` and `No Dementia`. The dataset itself is not included in this repository.

An 80:20 stratified image-level split was used:
- Training: 5,120 images
- Testing: 1,280 images

**Important limitation:** The split is image-level, not patient-level. If multiple scans from the same patient are present, images from one patient could appear in both sets. A patient-level split and independent validation are required for stronger scientific claims.

## Model and experiment configuration

| Setting | Value |
|---|---:|
| Input image size | 64 × 128, grayscale |
| Batch size | 32 |
| CNN training epochs | 10 |
| Adversarial training epochs | 10 |
| Optimizer | Adam |
| Learning rate | 0.001 |
| FGSM epsilon | 0.1 |
| Adversarial training ratio | 0.5 |
| Random seed | 42 |

The CNN uses three convolutional blocks (16, 32, and 64 channels), followed by a 128-unit fully connected layer and a two-class output layer.

## Recorded results

Results below are from the uploaded notebook's completed run.

| Metric | Initial CNN | After adversarial training |
|---|---:|---:|
| Clean test accuracy | 86.33% | 89.92% |
| Test precision (weighted) | 86.34% | 90.00% |
| Test recall (weighted) | 86.33% | 89.92% |
| Test F1 (weighted) | 86.33% | 89.92% |
| Test loss | 0.2597 | 0.2999 |

### FGSM robustness comparison

| Evaluation | Accuracy |
|---|---:|
| FGSM before adversarial training | 11.56% |
| FGSM after adversarial training | 89.92% |

These values describe one experimental run at the configured epsilon. They are not a guarantee of robustness against other attacks, perturbation strengths, datasets, or clinical settings. The equality between post-training clean and FGSM accuracy should be independently rechecked with additional attack settings and evaluation checks.

## Repository structure

```text
Dementia-MRI-Adversarial-Robustness/
├── notebooks/
│   └── dementia_mri_adversarial_robustness.ipynb
├── results/
│   └── README.md
├── .gitignore
├── requirements.txt
└── README.md
```

## Run in Google Colab

1. Open the notebook in `notebooks/` using Google Colab.
2. Upload your dataset ZIP when prompted. The ZIP should contain the two class folders `Dementia/` and `No Dementia/`.
3. Select a GPU runtime (the recorded experiment used a Tesla T4).
4. Run the notebook cells from top to bottom.
5. The notebook mounts Google Drive and saves the trained model and JSON metrics under `MyDrive/Dementia_MRI_Results/`.

## Dependencies

See [requirements.txt](requirements.txt). Google Colab provides the notebook runtime and commonly preinstalled PyTorch/torchvision packages; install compatible versions for your own environment.

## Tools and libraries

- Python
- PyTorch and Torchvision
- Adversarial Robustness Toolbox (ART)
- NumPy, Matplotlib, Seaborn
- scikit-learn
- Google Colab

## Responsible use

MRI data can be sensitive. Do not commit private or identifiable scans, datasets without redistribution permission, model checkpoints containing sensitive information, credentials, or access tokens. Treat all outputs as experimental and seek appropriate clinical, ethical, and data-governance review before any real-world medical use.

## Author

Developed as an academic AI/ML project.
