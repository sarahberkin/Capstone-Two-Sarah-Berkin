<h1>Diabetes Prediction System</h1>

_Diabetes is a chronic disease where the pancreas either does not produce insulin or the body is not able to effectively use the insulin, causing dangerously high levels of blood glucose. Without treatment, acute diabetes can lead to death. Even with management, diabetes takes a toll over time on the person's nervous system, blood vessels, and eyesight. [[1]](https://www.who.int/news-room/fact-sheets/detail/diabetes) Type 1 diabetes typically has early age onset and the cause is currently unknown. Type 2 diabetes and Gestational diabetes, however, have known risk factors that be tracked such as smoking, obesity, physical inactivity, A1C, high blood pressure, and high cholesterol. [[2]](https://www.cdc.gov/diabetes/php/data-research/index.html) Monitoring the risk factors can help catch diabetes in the early stage or in some cases even mitigate the risk for people who are pre-diabetic. Today, approximately 8.7 million adults in the United States meet the criteria and are like diabetic, yet are undiagnosed and not receiving treatment. The objective of this project is to develop a predictive model that can accurately identify individuals at risk of diabetes, thereby facilitating early intervention._

<h2>1. Data</h2>

The dataset used is originally from the National Institute of Diabetes & Digestive & Kidney Disease. The objective when they collected this data was to predict based on diagnostic measurements whether a patient has diabetes.

* [Kaggle Website Source](https://www.kaggle.com/datasets/mathchi/diabetes-data-set)
* [Kaggle Dataset](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/data/diabetes.csv)

<h2>2. Data Cleaning</h2>

[Data Cleaning Report](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Capstone%202%20Diabetes%20Project.ipynb)

* **Problem 1:** Inconsistencies in completeness of data entry. **Solution:** Null values were filled in with the mean or median, as appropriate for the various independent variables.
* **Problem 2:** Outliers were present throughout the independent variable values. **Solution:** Initial visualizations were done with histograms in order to get a sense of how far the distribution might be from normal. Outliers were later explored further using boxplots, then severe outliers were trimmed from the data.

![Boxplot](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/OutliersinBoxplot.png)

<h2>3. EDA</h2>

[EDA Report](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Sarah.Berkin--EDA-Capstone%202%20Diabetes%20Project.ipynb)

* Histograms were created to visualize the distribution of the variables after outliers were trimmed

![Histograms](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/Histograms.png)

* A heatmap was generated to visualize correlations between the variables

![Heatmap](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/CorrelationHeatmap.png)

* The 3 independent variables which had the lowest p-value from the Pearson Correlation Coefficient test were 1) Glucose, 2) Insulin, and 3) BMI

**Glucose P-value**

![Glucose P-value](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/Glucose%20Pearson%20Coefficient.png)

**Insulin P-value**

![Insulin P-value](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/Insulin%20Pearson%20Coefficient.png)

**BMI P-value**

![BMI P-value](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/BMI%20Pearson%20Coefficient.png)

<h2>4. Pre-Processing</h2>

[Pre-Processing Report](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/Sarah.Berkin--PreProcessing.Revised-Capstone%202%20Diabetes%20Project.ipynb)

* **Problem:** Out of the 768 people in the original sample, only 268 of them have diabetes. If the expressions of the dependent variable are not balanced in the dataset, it would be tough to get any model to accurately predict the outcome because the baseline would already be leaning towards a negative outcome. **Solution:** I created dummy variables in order to balance the dataset.

<h2>5. Modeling</h2>

_I used [scikit-learn](https://scikit-learn.org/stable/) for training my recommendation system. Based on the fact that my dependent variable, whether or not a person has diabetes, is a binary Yes/No, I determined that the 3 algorithms which made the most sense are 1) Logistic Regression, 2) Support Vector Machine (SVM), & 3) Gradient Boosting Classifier._

[Final Modeling Report with 3 Algorithm types](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/S.Berkin--Final-KFold-Capstone%202%20Diabetes%20Project.ipynb)

----

I first ran each algorithm by performing a train test split on the data to create training and testing clusters of the data. 

**Mean cross-validation & standard deviation when using Train Test Split**

![CVLR](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/MeansLogReg.wTTS.png)

![CVNext2](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/MeansSVM.GBC.wTTS.png)

**Accuracy & ROC-AUC CV with Train Test Split**

![Modeling Report with TTS](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/modelresultswithTTS.png)

-----

I next ran the same algorithms with K Fold cross validation to create clusters instead of train test split.

**Mean cross-validation & standard deviation when using K Fold CV**

![CV](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/3MeansWKFold.png)

**Accuracy & ROC-AUC CV with K Fold CV**

![Modeling Report with K Fold Cross-Validation](https://github.com/sarahberkin/Capstone-Two-Sarah-Berkin/blob/main/images/3modelresultsKFold.png)

--------

**Key Takeaways:**

* When using Train, Test, Split– SVM has the best Accuracy score & Gradient Boosting Classifier comes in second.
* When using Train, Test, Split– Gradient Boosting Classifier has the best ROC-AUC scores training scores, while SVM has the better ROC-AUC scores test scores.
* When  using Train Test Split, there does not appear to be any scenario that Logistic Regression is the best choice.
* When using K Fold Cross-Validation– Gradient Boosting Classifier has the best Accuracy & Logistic Regression comes in second.
* When using K Fold Cross-Validation– Gradient Boosting Classifier has the best ROC-AUC scores, while Logistic Regression comes in second. 

**Winning Model: Gradient Boosting Classifier with K Fold Cross-Validation** 

* For the sake of erring on the more conservative side, I will choose the K Fold CV. K Fold CV helps guard against overfitting and makes sure the entire dataset is used for training and testing while validating unseen data.
* Gradient Boosting Classifier model performed the best in both Accuracy & ROC-AUC CV.

<h2>Recommended Applications</h2>

Three recommended business objectives the predictive model developed in this project can support:

* **Targeted Marketing Campaigns:** Businesses can use the model to identify individuals at higher risk of diabetes and create tailored health and wellness campaigns. For example, companies offering health-related products or services could promote specific offerings, such as nutritious meal plans, fitness programs, or medical devices, to this audience.
* **Product Development & Innovation:** Companies in the healthcare and wellness industries could leverage the insights to develop new products that meet the needs of at-risk populations. This could include creating low-sugar food products, fitness tracking tools, or preventive health services, thereby opening new revenue streams.
* **Enhanced Customer Segmentation:** Insurance companies could integrate the model into their risk assessment processes to better segment customers. This could lead to more accurate pricing of health insurance policies and the development of personalized health management programs that reduce overall claims costs.

<h2>Future Improvements</h2>

* **Incorporate Additional Data:** Integrate more comprehensive datasets that include variables like family medical history, physical activity levels, and dietary habits.
* **Address Class Imbalance:** Apply techniques such as SMOTE (Synthetic Minority Over-sampling Technique) to balance the dataset and improve model performance on minority classes.
* **Feature Selection:** Utilize advanced feature selection methods to identify and retain the most impactful variables, potentially enhancing model efficiency and accuracy.
