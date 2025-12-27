<<<<<<< HEAD
# Conditional Stacked GAN with Skip-thought Vectors
### Text to Image Synthesis
---
#### Dependencies
```
tensorflow
numpy
progressbar
python-dateutil
easydict
pandas
torchfile
requests
Theano
gensim
pydot
pandas
Pillow
nltk
skipthoughts
```
### Setup
```
- The project is done in google colaboratory.
- The text embedding of data is downloaded from https://drive.google.com/u/0/uc?id=0B3y_msrWZaXLT1BZdVdycDY5TEE&export=download
and saved in Data folder.
- Unzip the data to Data/birds.
- The dataset CUB-200 is downloaded from the site http://www.vision.caltech.edu/visipedia/CUB-200.html.
- The downloaded dataset is saved in the folder Data/birds.
```
# ST-CSGAN — Conditional Stacked GAN with Skip-thought Vectors

Text-to-image synthesis project that implements a stacked conditional GAN (two-stage) guided by skip-thought text embeddings. The codebase trains on the CUB-200 birds dataset and can generate bird images conditioned on text descriptions.

## Highlights
- Two-stage conditional GAN (stage-1 and stage-2) for higher-fidelity image generation
- Uses skip-thought vectors as sentence embeddings for conditioning the generator
- Demo scripts for generating images from text descriptions
- Inception score utilities included under `Inception Score/` for evaluation

## Requirements
- Python 3.6 - 3.8 (project dependencies include TensorFlow and Theano; confirm compatible versions for your environment)


Primary Python dependencies are listed in `requirements.txt`. Install them with:

```bash
pip install -r requirements.txt
```



## Dataset
This project uses the CUB-200-2011 (Caltech-UCSD Birds) dataset.

- Download CUB-200: http://www.vision.caltech.edu/visipedia/CUB-200.html
- Place/untar the dataset so that images and metadata are available under `data/` or `Data/birds/` (the code expects `Data/birds` by default).

Additionally, skip-thought text embeddings are expected. The original project used precomputed skip-thought embeddings — a sample link used previously:

Download pretrained models (ST-CSGAN and Inception) from the provided link
https://drive.google.com/drive/folders/1GyapYRubGsQ0KTDsFryj6AdCif5Gqikq?usp=drive_link



1. Install dependencies

```bash
pip install -r requirements.txt
```

2. Prepare dataset and embeddings

- Put the CUB images and text annotations into `Data/birds/` (or update paths in `configuration.py` / `datasets.py`).
- Place precomputed skip-thought embeddings in `Data/` (or the path used by preprocessing).

3. Preprocess the dataset

```bash
python preprocess.py
```

This step builds any necessary mappings, extracts/loads embeddings, and prepares HDF5 or numpy files the trainers expect.

4. Train stage-1 model

```bash
python exp1.py
```

This trains the first stage. Models are saved to the `models/` directory by default.

5. Train stage-2 model (refinement)

```bash
python exp2.py
```

6. Run colab.ipynb to run the code in google colab

7. Generate images from example captions

Edit `Data/example_captions.txt` to add the descriptions you want to use for creating the image:

```bash
python demo.py
```

Generated images and intermediate outputs will be written to the configured output folders (check `demo.py` and `configuration.py`).

## Evaluation
The `Inception Score/` folder contains code and scripts to compute the Inception Score for generated images.



## Configuration
Edit `configuration.py` to change dataset paths, model hyperparameters, and training options. Many scripts read values from this file or from `custom.py`/`easydict` style settings.

## Notes, assumptions and troubleshooting
- The original code was developed and tested in Google Colaboratory. Some paths and environment assumptions reflect that. If you run locally, adjust paths in `configuration.py`.
- The code references both TensorFlow and Theano in `requirements.txt`. Use Python versions and package versions compatible with the models. Consider creating a dedicated virtualenv or conda environment.
- If you see missing-package errors for `skipthoughts` or `torchfile`, install them separately or use the versions in `requirements.txt`.

