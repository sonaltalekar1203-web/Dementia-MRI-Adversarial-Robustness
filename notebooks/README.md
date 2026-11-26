# Notebook

The main experiment notebook is intended to run in Google Colab with a GPU runtime.

## Dataset layout

Upload a ZIP archive containing the two class folders:

```text
dataset/
├── Dementia/
└── No Dementia/
```

The notebook's upload step places the archive at `/content/dataset.zip`.

## Execution

1. Open the notebook in Google Colab.
2. Select a GPU runtime (the recorded run used an NVIDIA Tesla T4).
3. Run the upload cell and select your dataset ZIP.
4. Run the experiment cell.
5. The notebook mounts Google Drive and saves the model and JSON result files in `MyDrive/Dementia_MRI_Results/`.

Do not upload private MRI scans or datasets unless you have permission to share them. The dataset is intentionally excluded from this repository.
