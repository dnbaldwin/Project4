# Project4
UniSA bootcamp (Individual) Project 4

This project uses ML tools to examine variability patterns in human fetal heart rate data during labour
The data were acquired using cardiotocograph (CTG) recordings, the dataset is online and available online
for training and learning purposs through the UC Irvine Machine Learning Repository.

Data Source:

https://archive.ics.uci.edu/dataset/193/cardiotocography

A powerpoint presentation of the workflow and results of the analysis is provided in this github repository.

Dataset Information:

1. The original dataset downloaded is an xls file (CTG_original_dataset.xls). ctg_orig.csv is the export of this file.

2. The original dataset required removal of formatting information and additional data under the table. This data is CTG3.csv. This is the initial useable dataset for the remainder of the analysis.

Dataset Preprocessing:

1. The dataset was preprocessed in Juypter notebook with (data_1_preprocessing.ipynb).
    - remove of unnecessary data columns
    - isna(), dropna() and data summary functions

    - This refined and cleaned dataset is data_preprocessed.csv

2. project4_0_NSP_categories.ipynb
    - preliminary look at target outcome measures. The NSP column represents the outcome of the CTG recording as follows: N; Normal, S; Suspicious, P; Pathological. The traces included in the recording were examined by experts and machine (The CTG device itself) to provide the information listed in the dataset.

Feature Set:

1. The xls File containing the dataset also contains an information page with explanation and definition of abbreviations, and the feature set. As many of the dataset columns contained data not relevant to the current analysis, these were removed. A modified featureset comprising the following was used for the analysis:
    ALTV - % time spent with abnormal long term variability of heart rate
    MLTV - the average value of long term variability
    ASTV - % time spent with abnormal short term variability of heart rate (i.e. beat-to-beat)
    MSTV - the average value of short term variability

Dataset Separation:

1. From the refined dataset (data_preprocessed.csv) a block of data containing the three outcome measures of interest was removed. The dataset comprised 30 recordings, with 'NSP' outcomes of each of the target measures: Normal, Suspicious, Pathological. Analyses where all three outcome measures were included have the _NSP in the filename.

2. During the analysis process it became apparent that three outcome measures (i.e.  Normal, Suspicious, Pathological) may have been complicating the models. As a result, analyses were repeated with Suspicious and Pathological outcomes grouped together into a single 'Abnormal' outcome variable. This provided a binary outcome measure of Normal/Abnormal. The files where this target outcome was used have _NP in the filename. The csv for this analysis was created using (project4_0.1_NSP_make_normal_path_csv.ipynb).

Dataset Analysis Workflow:

1. Random Forest modelling was undertaken initially, to identify the Feature Importances. This is where the ALTV/MLTV/ASTV/MSTV featureset was derived. Baseline heart rate (LB) is also a likely feature in this type of analysis and is thus used in some of the graphical comparisons (e.g. for clustering).

2. Clustering analysis was used with Kmeans to determine if features of heart rate variability were clustered for different outcome measures. This was observed to be the case.

3. Although, it was clear that three clusters were likely to be required, Elbow Curve was performed to confirm this.

4. Logistic regression analysis, train_test_split analysis and (briefly) SVM were performed to identify the accuracy of the models used. Several models were tested using both scaled (StandardScaler) and unscaled datasets.

Each of the Jupyter notebooks should run and select the dataset relevant to the analysis performed without need for alteration to the code.