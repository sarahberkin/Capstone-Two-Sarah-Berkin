<h1>#**Diabetes Prediction System**</h1>

-----------------------------------------

_Diabetes is a chronic disease where the pancreas either does not produce insulin or the body is not able to effectively use the insulin, causing dangerously high levels of blood glucose. Without treatment, acute diabetes can lead to death. Even with management, diabetes takes a toll over time on the person's nervous system, blood vessels, and eyesight. [[1]]([url](https://www.who.int/news-room/fact-sheets/detail/diabetes)) Type 1 diabetes typically has early age onset and the cause is currently unknown. Type 2 diabetes and Gestational diabetes, however, have known risk factors that be tracked such as smoking, obesity, phyisical inactivity, A1C, high blood pressure, and high cholesterol. [[2]]([url](https://www.cdc.gov/diabetes/php/data-research/index.html)) Monitoring the risk factors can help catch diabetes in the early stage or in some cases even mitigate the risk for people who are pre-diabetic. Today, approximately 8.7 million adults in the United States meet the criteria and are like diabetic, yet are undiagnosed and not receiving treatment. The goal here is to create a model that effectively predicts diabetes can be valuable and in doing so, improve outcomes and quality of life for the undiagnosed population._
##**1. Data**
The dataset used is originally from the National Institute of Diabetes & Digestive & Kidney Disease. The objective when they collected this data was to predict based on diagnostic measurements whether a patient has diabetes.
* [Kaggle Website Source]([url](https://www.kaggle.com/datasets/mathchi/diabetes-data-set))
* [Kaggle Dataset]([url](file:///users/sarahberkin/Downloads/diabetes.csv))
##**2. Data Cleaning**
[Data Cleaning Report]([url](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Capstone%202%20Diabetes%20Project.ipynb))
* **Problem 1:** Inconsistencies in completeness of data entry. **Solution:** Null values were filled in with the mean or median, as appropriate for the various independent variables.
* **Problem 2:** Outliers were present throughout the independent variable values. **Solution:** Initial visualizations were done with histograms in order to get a sense of how far the distribution might be from normal. Outliers were later explored further using boxplots, then severe outliers were trimmed from the data.
##**3. EDA**
[EDA Report]([url](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Sarah.Berkin--EDA-Capstone%202%20Diabetes%20Project.ipynb))
* The 3 independent variables which had the lowest p-value from the Pearson Correlation Coeficient test were 1) Glucose, 2) Insulin, and 3) BMI
![Glucose P-value](file:///Users/sarahberkin/Desktop/Screenshot%202025-02-28%20at%202.19.07%E2%80%AFPM.png)
![Insulin P-value](file:///Users/sarahberkin/Desktop/Screenshot%202025-02-28%20at%202.19.26%E2%80%AFPM.png)
![BMI P-value](file:///Users/sarahberkin/Desktop/Screenshot%202025-02-28%20at%202.19.42%E2%80%AFPM.png)
##**Pre-Processing**
[Pre-Processing Report]([url](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Sarah.Berkin--PreProcessing.Revised-Capstone%202%20Diabetes%20Project.ipynb))
* **Problem:** Out of the 768 people in the original sample, only 268 of them are have diabetes. If the expressions of the dependent variable are not balanced in the dataset, it would be tough to get any model to accurately predict the outcome because the baseline would already be leaning towards a negative outcome. **Solution:** I created dummy variables in order to balance the dataset.
##**Algorithms & Machine Learning**

##**Future Improvements**
##**Credits**
