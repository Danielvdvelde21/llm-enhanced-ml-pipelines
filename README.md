Master Thesis

Exploring LLM-Driven Enhancement Techniques for Machine Learning Pipelines Aimed at Improving Prediction Performance
Author: Daniel van der Velde

This repository contains the source code accompanying the master’s thesis report. The implementation reflects the framework and experimental setup described in the thesis, and is primarily written in Jupyter notebooks. The structure is organized by data modality and experimental design.

Repository Structure:

The repository is divided into three main directories, each corresponding to a data modality:
* Tabular/: Contains experiments and preprocessing scripts for tabular data.
  * Preprocessing/: Script to preprocess data
   
* Textual/: Contains experiments and preprocessing scripts for textual data.
  * Qualitative Loop/: Experiments with LLMS with validation
  * Non-Qualitative Loop/: Experiments with LLMs no validation
  * Preprocessing/: Script to preprocess data

* Image/: Contains experiments and preprocessing scripts for image data.
  * Ollama Only/: Experiments with VLLMs
  * Stable Diffusion/ Experiments with SD/GAN
  * Preprocessing/: Script to preprocess data

Each experiment is implemented in a standalone Jupyter notebook. Preprocessing scripts should be executed before running any experiments.

Prerequisites:

Data Requirements:

To reproduce the experiments, three datasets must be downloaded and placed in the corresponding directories:
* Tabular dataset: UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/2/adult 
* Textual dataset: IMDB Dataset of 50K Movie Reviews: https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews 
* Image dataset: House Prices and Images - SoCal: https://www.kaggle.com/datasets/ted8080/house-prices-and-images-socal

Each dataset should be stored in the appropriate modality directory. Both the preprocessing scripts and the experiment notebooks assume the data files are located within these directories. Similarly, the preprocessed data is expected to reside in the same folder as the corresponding experiment notebook.

Preprocessing:

Each data modality includes one or more preprocessing notebooks:
* Tabular Preprocessing.ipynb
* Tabular LLM Preprocessing.ipynb
* Textual Preprocessing.ipynb
* Image Preprocessing.ipynb

Run the relevant preprocessing notebook before executing experiments. Ensure the resulting preprocessed data is saved in the same directory as the associated experiment notebook.

Local LLM Setup with Ollama:

Experiments involving local (vision) large language models ((V)LLMs) require the installation of the Ollama interface. Note that all experiments in the thesis were executed using Ollama version 0.6.4. Please be aware that there are meaningful differences between versions, and compatibility cannot be guaranteed with newer releases.
Once Ollama is installed, required models will be downloaded automatically upon first use. This configuration supports most of the experiments in this repository, including those under the tabular, textual, and image (Ollama-based) directories.

Image Experiments and Model Weights:

Most image-based experiments using Stable Diffusion will run correctly once the appropriate Python dependencies are installed. However, the GAN-based image upscaling experiments require the manual download of model weights for RealESRGAN.
To trigger an automatic download of the RealESRGAN weights, modify the following line in the relevant image upscaling script:

model.load_weights('weights/RealESRGAN_x4.pth', download=False)
Change it to:
model.load_weights('weights/RealESRGAN_x4.pth', download=True)
This only needs to be done once.

Running the Experiments:

After having done the previous steps, all experiments can be run independently. Each notebook includes a clearly defined parameter section near the beginning, where key variables and configurations can be adjusted. The implications of these parameters are discussed in the thesis report.

Experimental Framework:

The underlying experimental design, including the distinction between qualitative and non-qualitative evaluation, model selection, and evaluation procedures, is described in detail in the thesis report. Please refer to the section titled "Experiments" for further insight into the structure and goals of each experimental code book.
For further clarification or details not included in this repository, consult the full thesis document.
