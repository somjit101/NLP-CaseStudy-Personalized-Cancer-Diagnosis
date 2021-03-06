# NLP CaseStudy - Personalized Cancer Diagnosis
In this problem statement, a sequence of genetic mutations and clinical evidences, i.e. descriptive texts from research literature as recorded by domain experts are used to classify the mutations to conclusive categories, to be used for diagnosis of the patient. 

## Overview

**The Kaggle page of this problem can be found [here](https://www.kaggle.com/c/msk-redefining-cancer-treatment/)**. 

The data has been provided by **Memorial Sloan Kettering Cancer Center (MSKCC)**

Here is the typical workflow :

### Context

1. A molecular pathologist selects a list of genetic variations of interest that he/she wants to analyze.
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
... | | |

**training_variants:**

ID  | Text
--- | --- 
0 | Cyclin-dependent kinases (CDKs) regulate a variety of fundamental cellular processes. CDK10 stands out as one of the last orphan CDKs for which no activating cyclin has been identified and no kinase activity revealed. Previous work has shown that CDK10 silencing increases ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2)-driven activation of the MAPK pathway, which confers tamoxifen resistance to breast cancer cells. The precise mechanisms by which CDK10 modulates ETS2 activity, and more generally the functions of CDK10, remain elusive. Here we demonstrate that CDK10 is a cyclin-dependent kinase by identifying cyclin M as an activating cyclin. Cyclin M, an orphan cyclin, is the product of FAM58A, whose mutations cause STAR syndrome, a human developmental anomaly whose features include toe syndactyly, telecanthus, and anogenital and renal malformations. We show that STAR syndrome-associated cyclin M mutants are unable to interact with CDK10. Cyclin M silencing phenocopies CDK10 silencing in increasing c-Raf and in conferring tamoxifen resistance to breast cancer cells. CDK10/cyclin M phosphorylates ETS2 in vitro, and in cells it positively controls ETS2 degradation by the proteasome. ETS2 protein levels are increased in cells derived from a STAR patient, and this increase is attributable to decreased cyclin M levels. Altogether, our results reveal an additional regulatory mechanism for ETS2, which plays key roles in cancer and development. They also shed light on the molecular mechanisms underlying STAR syndrome.Cyclin-dependent kinases (CDKs) play a pivotal role in the control of a number of fundamental cellular processes (1). The human genome contains 21 genes encoding proteins that can be considered as members of the CDK family owing to their sequence similarity with bona fide CDKs, those known to be activated by cyclins (2). Although discovered almost 20 y ago (3, 4), CDK10 remains one of the two CDKs without an identified cyclin partner. This knowledge gap has largely impeded the exploration of its biological functions. CDK10 can act as a positive cell cycle regulator in some cells (5, 6) or as a tumor suppressor in others (7, 8). CDK10 interacts with the ETS2 (v-ets erythroblastosis virus E26 oncogene homolog 2) transcription factor and inhibits its transcriptional activity through an unknown mechanism (9). CDK10 knockdown derepresses ETS2, which increases the expression of the c-Raf protein kinase, activates the MAPK pathway, and induces resistance of MCF7 cells to tamoxifen (6).
... |


**There are 9 different classes a genetic mutation can be classified into. Hence, this is a Multi class classification problem**

## Performance Metrics

([Source](https://www.kaggle.com/c/msk-redefining-cancer-treatment#evaluation))

Metric(s): 
* Multi class log-loss 
* Confusion matrix 

## ML Objective/Constraints

**Objective:** Predict the probability of each data-point belonging to each of the nine classes.

**Constraints:**

* Interpretability
* Class probabilities are needed
* Penalize the errors in class probabilites => Metric is Log-loss
* No Latency constraints

## Train, CV and Test Datasets

Split the dataset randomly into three parts train, cross validation and test with 64%,16%, 20% of data respectively.


## Classifiers Used for the Task 

Here, we have performed an analysis of the performance of the following classifiers individually, on the full, pre-processed datatset :
(Classifer Models Calibrated with **Sigmoid Calibration** as and when required and performed **Hyperparameter Tuning**)

1. Multinomial Naive Bayes' Theorem
2. K-Nearest Neighbors Classifer
3. Logistic Regression (One-vs-Rest)
4. Linear SVM
5. Random Forest Classifier

### Ensemble

Finally, all these classifiers are **combined** in the following manners for testing :

1. **Stacking Classifer** with Logistic Regression as the meta-classifier
2. **Maximum Voting Classifier**
