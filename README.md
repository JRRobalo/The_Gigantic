# The_Gigantic
Kaggle's "Titanic - Machine Learning from Disaster" competition
***
The titanic sunk. Many died.\
Can we <b>predict those who survived</b>?

<b>Strategy:</b>
* Feature extraction is largely automated;
* Main features are based on modifications/combinations of 
    * PCLASS (passenger ticket class), 
    * SEX (passenger gender), 
    * EMBARKED (port where passengers came aboar the Titanic), 
    * CHILD (whether the passenger is or not aged up to five years old), 
    * TITLE (passenger title extracted from name), 
    * FAMILY (SIBSP and PARCH, related to total number of the passengers' spouses, siblings, parents, and children aboard the Titanic), and 
    * FARE (ticket price);
* the data was modeled with a cross-validated Logistic Regression, with a final f1 score of 0.86 (died) and 0.69 (survived);
* the Kaggle score on the (unseen) dataset is 0.79 (top 8% as of submission date).
***
<b>Classification report for predictions on trial data (split from the provided training data):</b>

                              precision    recall  f1-score   support

    Predicted not to survive       0.78      0.96      0.86       137
        Predicted to survive       0.91      0.56      0.69        86

                    accuracy                           0.81       223
                   macro avg       0.84      0.76      0.78       223
                weighted avg       0.83      0.81      0.79       223
***
The model seems to perform poorly when predicting who survived (f1 score of 0.69). However, the training and (unseen) test data seem to have different distributions of target classes, and/or features. Improving the prediction of who survived can be attained by overfitting the data (drastically lowering predictions on test set) or by imputing ordinal features (like setting the CABINID, the FARE/AGE quartiles, etc to numerical values). The current approach is sufficiently automated and "trick"-free.
