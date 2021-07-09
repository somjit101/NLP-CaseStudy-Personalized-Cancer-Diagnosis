# NLP CaseStudy - Personalized Cancer Diagnosis
In this problem statement, a sequence of genetic mutations and clinical evidences, i.e. descriptive texts as recorded by domain experts are used to classify the mutations to conclusive categories, to be used for diagnosis of the patient. 

## Overview

The Kaggle page of this problem can be found [here](https://www.kaggle.com/c/msk-redefining-cancer-treatment/). 

The data has been provided by **Memorial Sloan Kettering Cancer Center (MSKCC)**

Here is the typical workflow :

### Context

1. A molecular pathologist selects a list of genetic variations of interest that he/she want to analyze.
2. The molecular pathologist searches for evidence in the medical literature that somehow are relevant to the genetic variations of interest.
3. Finally this molecular pathologist spends a huge amount of time analyzing the evidence related to each of the variations to classify them


Our goal here is to replace step 3 by a machine learning model. The molecular pathologist will still have to decide which variations are of interest, and also collect the relevant evidence for them. But the last step, which is also the most time consuming, will be fully automated.

### Problem Statement

Classify the given genetic variations/mutations based on evidence from text-based clinical literature.

## Useful Links

* [News Article](https://www.forbes.com/sites/matthewherper/2017/06/03/a-new-cancer-drug-helped-almost-everyone-who-took-it-almost-heres-what-it-teaches-us/#2a44ee2f6b25)
* [Video 1](https://www.youtube.com/watch?v=UwbuW7oK8rk)
* [Video 2](https://www.youtube.com/watch?v=qxXRKVompI8)

## Dataset Details

[Dataset Link](https://www.kaggle.com/c/msk-redefining-cancer-treatment/data)

- We have two data files: one conatins the information about the genetic mutations and the other contains the clinical evidence (text) that  human experts/pathologists use to classify the genetic mutations. 
- Both these data files are have a common column called ID
- <p> 
    Data file's information:
    <ul> 
        <li>
        training_variants (ID , Gene, Variations, Class)
        </li>
        <li>
        training_text (ID, Text)
        </li>
    </ul>
 </p>

### Example Datapoints

**training_variants:**

ID  | Gene | Variation | Class
--- | --- | --- | ---
1 | CBL | W802* | 2
2 | CBL | Q249E | 2

**training_variants:**

ID  | Gene | Variation | Class
--- | --- | --- | ---
1 | CBL | W802* | 2
2 | CBL | Q249E | 2
