# AI-Based Symptom Extraction System (Name Entity Recognition)
### Abstract
Extracting symptom information from the electronic health record (EHR) is a task that healthcare
providers and researchers regularly deal with. Traditionally, symptom extraction is a manual
search process that costs time and human efforts. With the increasing use of EHR data in routine
hospital encounters and clinical visits, evidence suggests that healthcare providers are at a higher
risk for EHR burden and burnout. This is true, especially during the COVID-19 pandemic. In
fact, time spent on analyzing EHR data increased by 157% compared to the pre-pandemic average.
How to quickly identify patient symptom information from EHRs is thus of paramount importance
for increasing healthcare providers productivity and reducing the burnout rate. In this research,
we propose a deep learning-based framework that combines customized word embedding
techniques and deep neural networks for symptom extraction. Using the Medical Information Mart
for Intensive Care (MIMIC-II) Database, we experiment various models with different
combinations of word embeddings plus a bidirectional long short-term memory (biLSTM) neural
network to automate symptom extraction. The best-performing model achieves an F1 score of
0.956 using a pre-trained GLoVe embedding concatenated with a self-trained FastText embedding
plus a biLSTM neural network classifier. This model efficiently extracts symptom information
and outperforms the benchmarks by more than 10%. Adopting such a fast and accurate system
can potentially reduce EHR burden and improve healthcare and research.

#### Note: Published paper is uploaded in the repository

## Folder/File Explanation
### _"records" Folder_
This folder contains all the eletronic health record files provided by n2c2 NLP Research Data Set. Each record contains deidentified patient information in the form of text. The name for each file the the patientID for each patient.

### _"annotationsRef" Folder_
This folder contains the indices of symptom words for each patient record. Use patientID to match records with their respective identified symptom words. Each symptom word was identified by hand by physicians who followed a thorough guideline. Here is the paper [DOI: 10.1016/j.jbi.2019.103354](https://www.sciencedirect.com/science/article/pii/S153204641930276X).

### _"annotationsAns" Folder_
This folder contains the name of each identified symptom word for each patient record based off the files in folder "annotationsRef". 

### _"processAll" File_
This python file, coded in jupyter notebook, preprocesses and concatenates all the records based off folders _"records"_, _"annotationsRef"_, and _"annotationsAns"_ to create a full dataset that can be used for Natural Language Processing (NLP) and Name Entity Recognition (NER). The full preprocessed dataset, if you choose not to run this file, is already provided and can be downloaded in file _"dataset.csv"_

### _"dataset" File_
This dataset contains three columns: Sentence, Word, and Tag. The sentence column is used to categorize each word into a given sentence. The word column contains all words used in each EHR. The tag column tags each word as either 0 or 1 (0 means non-symptom word; 1 means symptom word).

### _"GRU + Fine-Tuned Embeddings" File_
This python file, coded in jupyter notebook, creates the best-performing deep learning model proposed in our research paper. You can run this code to train your own model or you can load our best performing model using file _"model1.h5"_.

### _"BestModel"_ File
This h5 file is the exported model created from file _"GRU + Fine-Tuned Embeddings"_. 

### _"embedding" Folder_
