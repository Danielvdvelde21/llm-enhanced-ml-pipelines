# Master Thesis

**Exploring LLM-Driven Enhancement Techniques for Machine Learning Pipelines Aimed at Improving Prediction Performance**

**Author:** Daniel van der Velde

This repository contains the source code accompanying the master's thesis. The implementation reflects the framework and experimental setup described in the thesis and is primarily organized using Jupyter Notebooks.

## Repository Structure

The project is structured by data modality, with each directory containing preprocessing and experiment notebooks:

```
.
├── Tabular/
│   └── Preprocessing/
├── Textual/
│   ├── Qualitative Loop/
│   ├── Non-Qualitative Loop/
│   └── Preprocessing/
├── Image/
│   ├── Ollama Only/
│   ├── Stable Diffusion/
│   └── Preprocessing/
```

* **Tabular/**: Tabular data experiments
* **Textual/**: Text-based experiments, split by data generation method (qualitative vs. non-qualitative)
* **Image/**: Visual experiments using local VLLMs, GANs, and Stable Diffusion

## Prerequisites

### Data Requirements

To reproduce the experiments, download the following datasets and place them in their respective preprocessing subdirectories:

* **Tabular**: [UCI Adult Dataset](https://archive.ics.uci.edu/dataset/2/adult)
* **Textual**: [IMDB 50K Movie Reviews](https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews)
* **Image**: [House Prices & Images (SoCal)](https://www.kaggle.com/datasets/ted8080/house-prices-and-images-socal)

### Preprocessing Notebooks

Each modality includes one or more preprocessing notebooks. Run these before executing any experiments:

* `Tabular Preprocessing.ipynb`
* `Tabular LLM Preprocessing.ipynb`
* `Textual Preprocessing.ipynb`
* `Image Preprocessing.ipynb`

The preprocessed data outputs must be moved to the same directory as the corresponding experiment notebooks.

## Local LLM Setup (Ollama)

Experiments depend on locally hosted large language or vision-language models via [Ollama](https://github.com/ollama/ollama/releases).

All experiments in the thesis were conducted using **Ollama v0.6.4**. Compatibility with newer versions may vary.
Once installed, Ollama will automatically download any required models upon running the experimental code books.

## Image Experiments and Model Weights

Most image-based experiments using Stable Diffusion will work once the necessary Python dependencies are installed.

However, GAN-based upscaling experiments using RealESRGAN require manual weight downloads. To trigger this automatically, update the following line in the relevant notebook:

```
model.load_weights('weights/RealESRGAN_x4.pth', download=False)
```

to

```
model.load_weights('weights/RealESRGAN_x4.pth', download=True)
```

This only needs to be done once.

## Running the Experiments

Each notebook is self-contained and can be executed independently. A parameter configuration section is provided near the beginning of each file.
Adjust parameters as needed. Their impact is discussed in the thesis.

## Experimental Framework

The underlying experimental framework, including evaluation loops, model selection, and assessment strategies, is explained in the thesis.
Refer to the section titled **"Experiments"** for full context on the setup and structure.

For further clarification or details not included in this repository, consult the full thesis document.
