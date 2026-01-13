# Genomic Foundation Model Interpretability (ClinVar + NTv2 + Sparse Autoencoder)

This repo contains a small, reproducible pipeline to:
1) Load **ClinVar** variants (via the **GV-Rep / genomic-FM** dataset wrapper),
2) Train a lightweight **variant classifier head** on top of **Nucleotide Transformer v2 (NTv2)** embeddings,
3) Perform **mechanistic interpretability** by training a **Sparse Autoencoder (SAE)** on NTv2 hidden-layer activations, and
4) Visualize **feature activations** and **REF vs ALT activation differences** as per-token heatmaps.

> **Core idea:** represent each variant as *(REF sequence context, ALT sequence context, variant_type)* and predict ClinVar **CLNSIG**. Then use an SAE to discover sparse, interpretable directions in NTv2 activations and localize where those features fire on sequence tokens.

## Model diagram

![Model diagram](Figures/Model_Architecture.png)


---

## Contents
- `UHN_Technical_Test_Mark_Stevens.ipynb` - Central notebook to run this code
- `Stevens_Mark_Genomic_Interpretability.pdf` - PDF report detailing results
- `Figures/` All figures included in the report (plus additional ones!)

- In the "Releases", see `Model Training` to download a zip file with the models I previously trained, and run inference on them. You will need to unpack the zip file, and import it into your google drive in `uhn_models/model_4`. From there, you will be able to run inference on the previously trained models.
---

## Setup (Google Colab recommended)
Visit the link [HERE](https://colab.research.google.com/drive/1b4-ThzX9yowckrTCJwByS3hHbVdBGuR8?usp=sharing) https://colab.research.google.com/drive/1b4-ThzX9yowckrTCJwByS3hHbVdBGuR8?usp=sharing and make a copy. The Notebook will walk you through how to execute the code.

### NOTE:
- If you want to save the dataset on your Google Drive so you don't have to constantly redownload, you will need at least 11GB of space on your Drive.
- If you would like to train the full model, you will need a GPU with at least 80GB of VRAM. This model was trained on an A100 with Colab Pro. You can, however, chose smaller models (change `MODEL_NAME = "InstaDeepAI/nucleotide-transformer-v2-50m-multi-species`), choose a smaller dataset (Set `NUM_RECORDS=10000`), or decrease the sequence length (set `SEQ_LEN=512`).

# Author
- Mark Stevens
