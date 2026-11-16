# Skin Lesion Classification with GAN-Based Data Augmentation

An experimental deep-learning project exploring whether synthetic dermoscopic images can help address class imbalance in the HAM10000 skin-lesion dataset.

**Status:** research/portfolio prototype — not a clinically validated diagnostic system.

## Project overview

The repository contains:
- Baseline classifiers (ResNet-18 and MobileNetV2) trained on the original imbalanced data.
- Class-specific DCGAN experiments for `akiec`, `bcc`, `df`, `mel`, and `vasc`.
- An auxiliary-classifier GAN (ACGAN) experiment for class-conditioned image generation.
- A CNN experiment trained with real training images plus selected DCGAN-generated images.
- Data preparation and evaluation notebooks.

The HAM10000 task contains seven diagnostic labels: `akiec`, `bcc`, `bkl`, `df`, `mel`, `nv`, and `vasc`.

## Repository structure

```text
.
├── README.md
├── requirements.txt
├── .gitignore
├── CITATION.md
├── RESULTS.md
├── Final Project Report(2).pdf
├── notebooks/
│   ├── Baseline_Model_.ipynb
│   ├── dataprep.ipynb
│   ├── DCGAN_akiec.ipynb
│   ├── DCGAN_bcc.ipynb
│   ├── DCGAN_df.ipynb
│   ├── DCGAN_mel.ipynb
│   ├── DCGAN_vasc.ipynb
│   ├── Final ACGAN.ipynb
│   └── CNN_Model.ipynb
└── docs/
    └── RESEARCH_NOTES.md
```

## Dataset

The notebooks use the **HAM10000** dataset. The dataset images are not included in this repository. Download the dataset from the source below and arrange the files as described in the relevant notebook.

- Dataset: [HAM10000 on Kaggle](https://www.kaggle.com/datasets/kmader/skin-cancer-mnist-ham10000)
- Original dataset paper: Tschandl, P., Rosendahl, C., & Kittler, H. (2018), *The HAM10000 dataset: A large collection of multi-source dermatoscopic images of common pigmented skin lesions*, Scientific Data, 5, 180161. https://doi.org/10.1038/sdata.2018.161

Please review the dataset's current terms/licence before downloading or redistributing it. Do not commit the dermoscopic image files to this repository.

## Environment

The notebooks were developed primarily in Google Colab and use PyTorch. A GPU is strongly recommended for GAN training.

1. Clone this repository.
2. Install the dependencies listed in `requirements.txt`.
3. Download HAM10000 separately.
4. Update the dataset paths in each notebook to match your environment.
5. Run the notebooks in numerical order where applicable. The baseline notebook is independent; the DCGAN notebooks are separate class-specific experiments; the ACGAN notebook is a separate comparison; the final CNN notebook expects the real and generated image folders to have been prepared.

Some notebooks contain Google Colab / Google Drive-specific paths and commands. They are retained as experimental notebooks and need path adaptation before running locally.

## Current reported results

See [RESULTS.md](RESULTS.md) for the metrics recorded in the supplied notebooks and project report. These results are presented as separate experiments, **not as a controlled head-to-head comparison**: the baseline and augmented CNN notebooks use different train/validation/test split sizes and different classifier architectures.

## Important limitations

- The reported augmented CNN result is 78.02% test accuracy with 0.5471 macro F1. The report's claim that augmentation improves overall performance is not established by the available evidence.
- The baseline ResNet-18 result recorded in its notebook is 80.94% test accuracy with 0.6942 macro F1, but it uses a different test split; do not compare these values as if they came from the same experiment.
- The ACGAN notebook records a global FID of 96.992. FID alone does not establish clinical realism or usefulness.
- No Grad-CAM implementation or result was found in the supplied notebooks. Do not claim Grad-CAM was performed unless you add and run it.
- **Potential test-data leakage:** the class-specific DCGAN notebooks load class folders directly, while the augmented-CNN notebook creates its train/validation/test split later. Unless those GAN input folders were already restricted to training images, the generators may have been trained on images that later appear in validation/test. This must be resolved before reporting the augmented model's test metrics.
- No independent external validation, prospective clinical evaluation, or clinician assessment is included.
- The model must not be used for diagnosis or treatment decisions.

## Reproducibility and interpretation

The notebooks are preserved as cleaned versions of the supplied experiments: cell outputs and execution counters have been cleared to reduce repository size. The code has not been fully refactored or re-executed in a fresh environment. Some paths and Colab-specific operations still require adaptation.

## Contributors

Add the names of all project contributors here, and confirm permission before publishing group work. The original report includes student email addresses; do not publish those addresses without the owners' consent.


## Project report

The original academic project report is included as `Final Project Report.pdf`.
Before making this repository public, review the report for personal contact details
and confirm that all project contributors agree to public sharing.
