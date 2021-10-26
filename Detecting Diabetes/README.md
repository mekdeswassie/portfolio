# Detecting Diabetes 

### Problem Statement:

Diabetes is one of the main causes of death in the United States. Identifying and predicting this disease in individuals is the first step towards stopping its progression. In this project, we want to identify features that can be added to a health app that predicts diabetes and recommends interventions to individuals based on the outcome. We evaluate the capabilities of machine learning models in detecting at-risk individuals using survey data (and physical examination results), and identify key variables within the data contributing to this disease among the participants. The model will be evaluated based on recall and accuracy. 

### Background

> What is Diabetes?

Diabetes is a long-lasting health condition that affects how our body turns food into energy.Most of the food you eat is broken down into sugar (also called glucose) and released into your bloodstream. When your blood sugar goes up, it signals your pancreas to release insulin. Insulin acts like a key to let the blood sugar into your body’s cells for use as energy.

If you have diabetes, your body either doesn’t make enough insulin or can’t use the insulin it makes as well as it should. Insulin is a hormone that regulates blood sugar level. When there isn’t enough insulin or cells stop responding to insulin, too much blood sugar stays in our bloodstream. Over time, that can cause serious health problems, such as heart disease, vision loss, and kidney disease. There isn’t a cure yet for diabetes, but life style changes such as losing weight and being active can really help.



### Methodology

We utilized supervised machine learning models to identify individuals with diabetes. Using the National Health and Nutrition Examination Survey (NHANES) dataset, we conduct an exhaustive search of all available feature variables within the data to develop models for diabetes detection. 

Using different time-frames and feature sets for the data (based on laboratory data), multiple machine learning models (logistic regression, support vector machines, random forest, and gradient boosting) were evaluated on their classification performance. The models were then combined to develop a weighted ensemble model, capable of leveraging the performance of the disparate models to improve detection accuracy. Information gain of tree-based models was used to identify the key variables within the patient data that contributed to the detection of at-risk patients in each of the diseases classes by the data-learned models.


### Data Dictionary:
    
|Feature|Type|Dataset|Description|
|---|---|---|---|
|BMXBMI|float|NHANES/2017 - March 2020|Body mass index is a ratio of weight in kilograms to squared height in meters|
|BMXHIP|float|NHANES/2017 - March 2020|hip measurement|
|BMXWAIST|float|NHANES/2017 - March 2020|waist measurement|
|BPQ020|float|NHANES/2017 - March 2020|response to the question 'Have Dr. tell you have High blood pressure?'|
|BPXODI2|float|NHANES/2017 - March 2020|Diastolic blood pressure|
|BPXOSY2|float|NHANES/2017 - March 20|Systolic blood pressure|
|DIQ010|float|NHANES/2017 - March 2020|respondent response to the question 'Doctor told you have diabetes'|1-yes, 2-no|
|INDFMPIR|float|NHANES/2017 - March 2020|ratio of family income to poverty guidelines|0 to 4.98, 5 >= 5.00|
|RHQ160|float|NHANES/2017 - March 2020|respondent response to the question 'How many times have you been pregnant?'| 
|RIAGENDR|float|NHANES/2017 - March 2020|gender of the participant|1-Male 2-Female|
|RIDAGEYR|float|NHANES/2017 - March 2020|age of the participant in years at the time of screening|
|RIDRETH3|float|NHANES/2017 - March 2020|race of the participant| 1-Mexican American, 2-Other Hispanic, 3-Non-Hispanic White, 4-Non-Hispanic Black, 6-Non-Hispanic Asian, 7-Other Race (Including Multi-Racial)|
|MCQ300C|float|NHANES/2017 - March 2020|response to the question 'Do your close relative had diabetes?'|
|PAQ605|float|NHANES/2017 - March 2020|vigorous work activity|
|PAQ620|float|NHANES/2017 - March 2020|moderate work activity|
|PAQ635|float|NHANES/2017 - March 2020|walk or bicycle|
|PAQ665|float|NHANES/2017 - March 2020|moderate recreational activities|
|PAQ650|float|NHANES/2017 - March 2020|vigorous recreational activities|
|SMQ040|float|NHANES/2017 - March 2020|respondent response to the question 'Do you now smoke cigarettes?'|1-Every day, 2-Some days, 3-Not at all, 7-Refused, 9-Don't know|



### Summary of EDA
___

##### Statistics
- Average age is 37.9 which is kind of in the middle.
- Average BMI is 26.9. It is above 25 and so a higher number of the respondents could be overweight.
- Average wh_ratio is 0.85, which shows that a higher number of respondents could have abdominal obesity.
- Age, waist-hip ratio, waist and hip measurements, BMI, blood pressure and any kind of physical activity have a positive correlation with diabetes. Smoking status has a negative correlation with diabetes.
- BMI distribution is skewed to the left. Systolic and diastolic blood pressures have a normal distribution.
- A higher number of respondents with diabetes are 45 and older. But there are outliers; a few respondents of age 25 and younger have diabetes. 
- A higher number of diabetic respondents have a wh_ratio above 0.75.
- wh_ratio and BMI show a pattern which is expected as this body measurements can be indicative of one another.

##### Distribution of the data

1. Outcome Variable: The class distribution in the outcome column are not what we expected. There is a class imbalance; the positive class makes up only 12%
2. Pedigree

    - Comparing to participants with no known close relative who is diabetic, respondents with diabetic close relatives and who themselves are diabetic is three times the number. 
  
    - This is what we have expected since diabetes is a hereditary disease.
    
3. Gender: approximately 50 50 - its well balanced.

4. Race: We have uneven distribution of race. non-hispanic white makeup one third of respondents, followed by non-hispanic black making up one fourth of the respondents. Multi racial has the least number of representation. 

5. age: A higher number of respondents with diabetes are 45 and older. But there are outliers; a few respondents of age 25 and younger have diabetes. 

6. Body measures: BMI, wh_ratio: Diabetic class has a higher median value for BMI and wh_ratio as we expected. BMI of 30 for diabetic and BMI of 25 for non-diabetic 

7. blood pressure: Diabetic respondents have a higher systolic and dystolic blood pressure. There are more number of participants who diabetes and high blood pressure and diabetes comparing to people with no high blood pressure. 

8. physical activity: The number of diabetic people who do not do any physical activity be it at work or recreational, is higher than diabetic people who do some kind of physical activity.

11. number of pregnancies: Distribution is skewed to the left. Women with zero pregnancies have the highest number of diabetic respondents. Number of pregnancies of three and two have the highest number of diabetic women.

12. smoking: smoking data is imbalanced. we have 5X more respondents who are non-smokers and diabetic comparing to smokers and diabetic.

### Findings

If one has a high blood pressure, the odds of suffering from diabetes increases by 67%

If one has close relatives that are diabetic, the odds of being diabetic increases by 41%

If one has no close relatives that are diabetic, the odds of being diabetic decreases by 55%

As age increases by one year, the odds of being diabetic increases by 6%

As BMI increases by one unit, the odds of being diabetic increases by 6%

As number of pregnancy increases by one, the odds of being diabetic decreases by 5%

If you are non-hispanic white, the odds of getting diabetic decreases by 17%. 




### Conclusion/Recommendation

-High blood pressure and family history of diabetes are stronger predictors of diabetes. Age, BMI and number of pregnancies also have predictive power. 
- Therefore, these features may be added to the app.
- But this model is not perfect. It was trained on imbalance data so getting better data with equal representation of the two classes will help the model to better classify and minimize false positives and false negatives.



### Sources: 

- https://wwwn.cdc.gov/nchs/nhanes/continuousnhanes/default.aspx?cycle=2017-2020
- https://www.cdc.gov/healthyweight/assessing/bmi/adult_bmi/index.html
- https://www.hsph.harvard.edu/obesity-prevention-source/obesity-definition/abdominal-obesity/



