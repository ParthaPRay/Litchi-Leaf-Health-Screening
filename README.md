# Litchi Leaf Health Screening

**Developed by Partha Pratim Ray**

This repository presents a reproducible workflow for evaluating the reliability of litchi leaf health screening across independently collected field image datasets.

📓 [View the notebook](R1_Litchi_Cross_Dataset_GradCAM.ipynb)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ParthaPRay/Litchi-Leaf-Health-Screening/blob/main/R1_Litchi_Cross_Dataset_GradCAM.ipynb)

## What this work presents

The notebook trains MobileNetV3-Small and EfficientNetV2-S on BDLitchi images and evaluates their transfer to an independent Rangamati litchi collection.

The workflow includes:

- Dataset verification, image auditing, and image-family grouping.
- Classification of four provisionally aligned categories: healthy, insect damage, leaf blight, and red rust.
- Internal and external evaluation, confusion matrices, and precision–recall curves.
- Temperature calibration and confidence- and energy-based referral.
- Separate evaluation of additional and mixed-symptom categories.
- Image-family bootstrap intervals and paired statistical comparisons.
- Grad-CAM explanations and attribution-guided masking diagnostics.
- A Gradio interface displaying both models’ predictions, probabilities, referral decisions, explanations, and downloadable reports.

## Datasets

### BDLitchi — Version 1

Used as the source collection for training, validation, and internal testing.

- [Dataset page](https://data.mendeley.com/datasets/jhb24mszdk/1)
- DOI: **10.17632/jhb24mszdk.1**

Use the original image archive identified in the notebook.

### Rangamati — Version 3

Used for independent external evaluation. Only the lychee images from the mango, lychee, and jackfruit collection are used.

- [Dataset page](https://data.mendeley.com/datasets/94srbmydkw/3)
- DOI: **10.17632/94srbmydkw.3**

Dataset ownership and annotation credit belong to the original contributors. Please cite both dataset records when using this work.

## Main findings

| Model | Internal macro-F1 | External macro-F1 |
|---|---:|---:|
| MobileNetV3-Small | 0.9971 | 0.2057 |
| EfficientNetV2-S | 1.0000 | 0.2998 |

These results concern the initial external cohort of **2,774 images**.

Despite strong internal recognition, both models showed substantial external performance reductions. Neither recognized external leaf blight. Source-fitted temperature scaling worsened external probability quality, while referral scores provided limited separation of matched and additional categories.

The study demonstrates why internal accuracy should be assessed alongside external category-specific recognition, calibration, referral coverage, and false acceptance.

## Running the notebook

1. Open the notebook in Google Colab.
2. Select a GPU runtime; experiments used an NVIDIA T4.
3. Run the cells sequentially, following the dataset and path instructions.
4. Allow approximately **25 GB of free storage** for archives, extracted images, and outputs.
5. Download the generated results and model bundle before the Colab session ends.

Training and source partitioning use **seed 42**. The supplementary statistical analysis uses **seed 2026**.

## Using the Gradio interface

Upload a clear RGB photograph of a litchi leaf or select an included example. The interface evaluates both models separately and displays their candidate categories, probabilities, referral decisions, and Grad-CAM overlays.

A retained prediction indicates that the selected threshold was satisfied. It does not establish a correct diagnosis. Outputs represent the four trained visual categories; the system does not independently confirm pathogens, species, or symptom severity.

## Credit

**Partha Pratim Ray**  
Department of Computer Applications  
Sikkim University, Gangtok, India

If you use this notebook or adapt its workflow, please acknowledge Partha Pratim Ray, link to this repository, and cite the original datasets.

Repository: https://github.com/ParthaPRay/Litchi-Leaf-Health-Screening
