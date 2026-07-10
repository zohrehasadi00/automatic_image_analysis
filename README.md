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
├── models
│   └── modern pipeline models
│  
└── README.md
</pre>

The only part you definitly need is the HAM10000 dataset. This can bedownloaded [here](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/DBW86T). Create a dir for the project, inside a data dir, in the data dir the raw dir and then extract the images into the raw dir in the two seperate folders. 

## SkinLesionTriage
In the jupyter notebook "skinLesionTriage" under notebooks you find the data pre processing. Check if your file path is set correctly and run the notebook from top to bottom. It will create the splits for the train, validation and test sets and saves them in the splits dir. This part needs to be run at least once before using one of the pipelines.

## Classical pipeline

The classical pipeline can be found under notebooks. You need to check if the project dir is set correctly. Some of the data load variables could fail at the first run because the files are not created yet. 

For running the classical pipeline just run each cell after one another from top to bottom. 