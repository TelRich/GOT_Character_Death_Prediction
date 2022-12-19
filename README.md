[Full Project](https://nbviewer.org/github/TelRich/GOT_Character_Death_Prediction/blob/main/got_prjt_v5.ipynb?flush_cache=True)
[Data Cleaning and Feature Engineering](https://nbviewer.org/github/TelRich/GOT_Character_Death_Prediction/blob/main/GOT-PT2_Data_Cleaning-Feat_Eng.ipynb?flush_cache=True)
[Machine Learning](https://nbviewer.org/github/TelRich/GOT_Character_Death_Prediction/blob/main/GOT-PT3_ML.ipynb?flush_cache=True)

## Summary
1. There were 38 battles fought within 3-year context of our data
2. Characters without alleigiance to any house has the highest death count, followed by the nights watch.
3. From the characters data, we have 128 dead women, 618 alive women, 367 dead men, and 838 alive men.
4. There is a 17% chance that a female record turns out dead, and there is 30.5% chance a male record turns out dead.
5. In other to link the battle and character death deatails to the characters data, 4 features were created.
    * Feature to show characters who were commanders.
    * Feature to show characters who belong to house of war attackers an defenders.
    * Feature to show characters who belong to one of the house of allegiance.
    * Feature to show characters who house swore alliegiance to another house.
>
6. The data was under sampled because of the label feature was imbalance 1,451 and 495 for alive and dead charaters respectively. After undersampling we had 500 and 495 for alive and dead characters respectively.
7. The data was trained on five (5) classification model, and the following score was gotten for each:

|Models|Train Score| Test_Score	|ROC_AUC Score|
|---|:---:|:---:|:--:|
|LogisticRegression	| 0.709770	| 0.648829 |	0.724318
|KNeighborsClassifier|	0.784483 |	0.682274 |	0.737987
|RandomForestClassifier|	0.896552 |	0.692308 |	0.746711
|DecisionTreeClassifier|	0.896552 | 0.675585 |0.697673
|XGBC	| 0.873563 | 0.688963 |	0.762461
>
8. Out of the five model, two of them (Random Forest Classifier and XGBClassifier) was performing better than the other, below is their performance on the test data:

Random Forest Classifier Test Performance: Accuracy 69%  

| Character | precision | recall | f1-score |
|---|---|---|---|
|Dead       |0.68  |    0.71  |    0.70   |    149
|Alive       |0.70|      0.67  |    0.69 |      150
>
XGBClassifier Test Performance: Accuracy 69%

|Character| precision | recall |  f1-score |
|---|---|---|---|
|Dead   |    0.67   |   0.73   |   0.70    
|Alive |       0.71  |    0.65   |   0.68  
>
9. Random Forest classifier was chosen as the model of interest, and its parameter was tuned using Random Search Cross Validation and Grid Search Cross Validaton, for best results. Below are the performance after tuning:
* Base Model Performance
>
>Average Error: 0.3077 degrees.
>
>Accuracy: 69.23%.

* Fine-Tuning Model 1 Performance (RandomSearchCV)
>
>Average Error: 0.3010 degrees.
>
>Accuracy: 69.90%.
>
>Improvement Error: -2.17%.
>
>Improvement Accuracy: 0.97%.

* Fine-Tuning Model 2 Performance (GridSearchCV)
>
>Average Error: 0.3077 degrees.
>
>Accuracy: 69.23%.
>
>Improvement Error: 0.00%.
>
>Improvement Accuracy: 0.00%.

* Fine-Tuning Model 3 Performance (GridSearchCV)
>
>Average Error: 0.2910 degrees.
>
>Accuracy: 70.90%.
>
>Improvement Error: -5.43%.
>
>Improvement Accuracy: 2.42%.

10. Using the best parameters from the last model tuning, we made some predictions and found out, based on the first ten rows, the model was performing well on characters that belongs to one of the house of allegiance.

* The error ratio for characters for characters who are commander is high (1.75) compared to characters who are not commander (0.50)

### Limitations
- Limited data. After feature selection, we found out that more than 50% of the features were dropped because some were leaaking data of the target variable, some had low correlation, and some had multicollinearity.
- We know most of of the characters died because of the different battles fought, but the link between the character data and battle data is not sufficient enough.
- Few people had an understanding of how to do EDA and build a model
- More commitment from members to push themselves to learn as well as to attend the group meetings.
