# Results recorded in the supplied project files

These values are transcribed from the supplied notebooks and report. They are **not a controlled comparison** because the experiments use different data splits and model architectures.

## Classifier results

| Experiment | Test images | Accuracy | Macro precision | Macro recall | Macro F1 |
|---|---:|---:|---:|---:|---:|
| ResNet-18 baseline (baseline notebook) | 1,002 | 0.8094 | 0.6693 | 0.7523 | 0.6942 |
| MobileNetV2 + focal loss (baseline notebook) | 1,002 | 0.7774 | 0.6139 | 0.6887 | 0.6373 |
| CNN with DCGAN augmentation (CNN notebook / report) | 992 | 0.7802 | 0.6392 | 0.5097 | 0.5471 |

The baseline notebook also records melanoma recall of 0.7054 for ResNet-18 and 0.5804 for MobileNetV2. The augmented CNN notebook reports melanoma recall of 0.3636 and dermatofibroma (`df`) recall of 0.0909.

## ACGAN result

- Global FID recorded by the ACGAN notebook: **96.9920** (using up to 1,000 real and 1,000 generated images as configured in the notebook).

## Interpretation

The current evidence does **not** support saying that GAN augmentation improved classification performance. The augmented CNN's macro F1 is lower than the recorded ResNet-18 baseline, but the experiments are not directly comparable because their test-set sizes/splits and classifier architectures differ. A fair claim requires rerunning baseline and augmented models using the exact same real train/validation/test split, identical classifier architecture, identical preprocessing, and a test set containing real images only.

The ACGAN FID score is a single global metric and should be interpreted cautiously. It is not a clinical validation metric and does not by itself prove that generated lesions are realistic or class-faithful.
