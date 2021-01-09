# Covid19-Data-Analysis
## Introduction  
As the social and economic impacts of COVID-19 are being felt, it is necessary to develop new approaches and products along the way to better serve people and deliver insights through data. The World Health Organization (WHO) characterized the COVID-19, caused by the SARS-CoV-2, as a global public health threat. The outbreak caused by the severe acute respiratory syndrome progressed within China and then beyond. This recent outbreak emphasizes the importance of analyzing the epidemiological data of this novel virus and predicting their risks of infecting people all around the globe.  

#### General context
On February 26 Brazil recorded its first case of SARS-CoV-2, and the virus transmission that was evolved from imported cases only rapidly spread to local and finally community leading the federal government to declare the nationwide community transmission on March 20. Until March 27, the state of São Paulo had recorded 1,223 confirmed cases of COVID-19, with 68 related deaths. While the county of São Paulo, with a population of approximately 12 million people and where Hospital Israelita Albert Einstein is located, had 477 confirmed cases and 30 associated deaths, as of March 23. With the lethality rate reaching 5.7 percent now, São Paulo remains the most affected state and decided to establish quarantine and social distancing measures starting from March 24 as an effort to slow the virus spread.
#### Purpose
The exponential increase in the number of cases overwhelmed the health systems around the world with rising demand for ICU beds and ventilators far above the existing capacity, Italy being a prominent example. The purpose of this project is to analyze the data of patients who visited the Hospital Israelita Albert Einstein and had their samples collected for SARS-CoV-2 RT-PCR testing. The idea is to develop a generalized classification model using ensemble learning methods like Trees that could be useful during routine clinical care, and although laboratory exams can be similar or vary for different individuals with the same or different condition, the aim is to focus on laboratory tests more commonly ordered during a visit to the emergency room for COVID-19 positive patients. The main motivation for the challenge is in the context to support the health systems by predicting confirmed cases among the suspected cases based on the results of the laboratory tests and then predicting the level of medical attention required like whether the patient among these confirmed cases needs to be admitted to general or regular ward, semi-intensive care unit or an intensive care unit(ICU).  With the possible limitations to perform tests for the detection of SARS-CoV-2, the reason for choosing this project was mainly to perform data analysis to support the frontline health workers to reach out with medical help to the actual needy as testing everyone would be impractical and tests results could be delayed even if only a target subpopulation would be tested.

## Dataset  
The dataset used for performing the analysis is sourced from a Kaggle challenge hosted by Einstein Data4u. The dataset contains anonymized data from patients belonging to Brazil’s São Paulo state and county collected from March 28th to April 1st. The numerous features represent various clinical laboratory data.  

#### Data Description
After importing the data, data contained 5644 observations of 111 variables.  

Below is the list of target variables as they are present in the dataset:
For Task1,  
SARS-Cov-2 exam result – contains 2 values: negative or positive  

For Task2,  
Patient addmited to regular ward: contains 2 values: 1=yes and 0=no  
Patient addmited to semi-intensive unit: contains 2 values: 1=yes and 0=no  
Patient addmited to intensive care unit: contains 2 values: 1=yes and 0=no  

There were variables related to collected data from test reults of blood samples, urine samples. Also, there were other variables that represented names of certain suspected viral infections, may be considered important for COVID19 testing. They gave a glimpse of a patient’s medical history. There are only 2 levels or values for all these variables: either ‘detcted’ or ‘not_detected’.  

## Methods Used  

For both the tasks, used ‘caret’ package to partition data such that 70% of the data is utilized for training and the rest is assigned to testing set.  

#### Models  
##### TASK1  
As the response variable for the task was binary with only 2 levels, was motivated to implement the following methodologies to build classifiers:  
•	Logistic regression  
•	Linear Discriminant Analysis (LDA)  
•	Quadratic Discriminant Analysis (QDA)  
•	Random Forest  

##### TASK 2  
The task was to predict which patients will need to be admitted to which emergency room. So, the response variable for the task had 3 levels, and to build the multi classifier was motivated to implement the following methodologies to train the statistical model:  
•	Multinomial classification  
•	Random Forest  
•	Non-linear Support Vector Machines (SVM)  
•	kNN  
Since, the response variable is a nominal one, trained the first classifier using the penalized nominal approach and then continued with the above llisted choice of ensemble learning methods.  

#### Evaluating Model Performance  
To evaluate and compare combined model performances so that the best model is chosen, resamples () was used with following metrics:  
•	AUC of ROC  
•	Sensitivity  
•	Specificity  
The best model was selected with the highest values of Area under ROC curve on test data. ROC was preferred over accuracy in this case as there was a skewed distribution of categorical classes for both the tasks so as to avoid the model to predict majority class each time and report false high accuracy.  

## Results  
Results were reported in detail in the code itself


