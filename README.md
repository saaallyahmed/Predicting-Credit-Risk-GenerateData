# Predicting-Credit-Risk-GenerateData
Supervised Machine Learning

LendingClub is a peer-to-peer lending services company that allows individual investors to partially fund personal loans as well as buy and sell notes backing the loans on a secondary market. LendingClub offers their previous data through an API.

We used the data to create machine learning models to classify the risk level of given loans. Specifically, Also comparing the Logistic Regression model and Random Forest Classifier.



### Retrieve the data

In the `Generator` folder in `Resources`, there is a [GenerateData.ipynb](/Resources/Generator/GenerateData.ipynb) notebook that will download data from LendingClub and output two CSVs: 

* `2019loans.csv`
* `2020Q1loans.csv`

We entire year's worth of data (2019) to predict the credit risk of loans from the first quarter of the next year (2020).

Note: these two CSVs have been undersampled to give an even number of high risk and low risk loans. In the original dataset, only 2.2% of loans are categorized as high risk. To get a truly accurate model, special techniques need to be used on imbalanced data. Undersampling is one of those techniques. Oversampling and SMOTE (Synthetic Minority Over-sampling Technique) are other techniques that are also used.

## Preprocessing: Convert categorical data to numeric

Create a training set from the 2019 loans using `pd.get_dummies()` to convert the categorical data to numeric columns. Similarly, create a testing set from the 2020 loans, also using `pd.get_dummies()`. Note! There are categories in the 2019 loans that do not exist in the testing set. If you fit a model to the training set and try to score it on the testing set as is, you will get an error. You need to use code to fill in the missing categories in the testing set. 

## Consider the models

We created and comparing two models on this data: a logistic regression, and a random forests classifier. How do the model scores compare to each other, and to the previous results on unscaled data?

Looks like the model for the linear regression got way better, but the random forest classifier remained spot on. From what I can tell, the random forest classifier did not benefit much from the scaling, whereas the linear regression did.
## Fit a LogisticRegression model and RandomForestClassifier model

We created a LogisticRegression model, fit it to the data, and print the model's score. We did the same for a RandomForestClassifier. 

Looks like I was totally underestimating the strength of scaling the data would do to the linear regression!

## Revisit the Preprocessing: Scale the data

The data going into these models was never scaled, an important step in preprocessing. Use `StandardScaler` to scale the training and testing sets. Before re-fitting the LogisticRegression and RandomForestClassifier models on the scaled data, we made another prediction about how we think scaling will affect the accuracy of the models.

Fit and score the LogisticRegression and RandomForestClassifier models on the scaled data. How do the model scores compare to each other, and to the previous results on unscaled data? How does this compare to your prediction? Write down your results and thoughts.


There is some strangeness to how I can run this whole notebook and get some significantly different values to the ones I have.



### References

LendingClub (2019-2020) _Loan Stats_. Retrieved from: [https://resources.lendingclub.com/](https://resources.lendingclub.com/)

- - -

© 2021 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

