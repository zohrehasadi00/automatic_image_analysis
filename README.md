# Automatic Image Analysis - Group 01: Topic B

## Data Structure
We used google colab for the project with a shared data folder. The structure inside of this folder was as followed: 

<pre>
dataFolder
├── data
│   └── raw
│        ├── HAM10000_images_part_1
│        │    └── Extracted Images
│        └── HAM10000_images_part_2
│             └── Extracted Images
│              
├── splits (The files will be created when running the pre processing)
│   ├── train.csv
│   ├── test.csv
│   └── val.csv
|
├── histogram
│   └── histograms will be saved here
└── models
    └── modern pipeline models

</pre>

The only part you definitly need is the HAM10000 dataset. This can bedownloaded [here](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/DBW86T). Create a dir for the project, inside a data dir, in the data dir the raw dir and then extract the images into the raw dir in the two seperate folders. 

## SkinLesionTriage
In the jupyter notebook "skinLesionTriage" under notebooks you find the data pre processing. Check if your file path is set correctly and run the notebook from top to bottom. It will create the splits for the train, validation and test sets and saves them in the splits dir. This part needs to be run at least once before using one of the pipelines.

## Classical pipeline

The classical pipeline can be found under notebooks. You need to check if the project dir is set correctly. Some of the data load variables could fail at the first run because the files are not created yet. 

For running the classical pipeline just run each cell after one another from top to bottom. 

## Modern Pipeline

Overview
This project implements a cost-aware deep learning pipeline for the automated triage of skin lesions. Utilizing an EfficientNet-B0 convolutional neural network (CNN), the system is specifically designed to handle asymmetric clinical costs. Furthermore, it integrates Monte Carlo (MC) Dropout to approximate Bayesian inference, providing predictive uncertainty estimates alongside binary diagnostic classifications (Benign vs. Malignant) on the HAM10000 dataset.

Execution Protocol
For successful reproduction, the notebook cells must be executed in the following sequential order. Note that the Frozen and Unfrozen backbone configurations are treated as strictly independent experiments to ensure unbiased evaluation.

Setup & Data Integration: Initialize the environment, mount Google Drive (if used), and verify that all data paths in the Data Loading section point to the correct local dataset and metadata CSV.

Experiment Selection (Frozen vs. Unfrozen): Execute the configuration for only one approach at a time.

Important: To ensure a fair comparison, always re-initialize the model from the pre-trained ImageNet state before starting a new training run. Training the unfrozen model immediately after the frozen one without resetting will lead to skewed results, as the weights are no longer in their baseline state.

Model Training: Execute the respective training loop (Frozen Backbone for classification head training OR Unfrozen Backbone for fine-tuning). The script features early stopping and automated model checkpointing. Ensure that your save_path is uniquely defined for each experiment to prevent overwriting.

Inference & Uncertainty Evaluation: Load the best-performing weights for the specified experiment and execute the MC Dropout inference module. This final step generates robust mean probabilities, uncertainty scores, and high-resolution diagnostic visualizations within the exports/ directory.
