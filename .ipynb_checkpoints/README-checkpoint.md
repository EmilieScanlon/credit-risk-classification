# credit-risk-classification

## Overview of the Analysis

Purpose and Data Summary
=
The purpose of the analysis is to determine whether the decision matrix used to classify borrowers as either healthy or high-risk accurately represents all borrowers. Specifically, this analysis aims to evaluate if the predictive model effectively categorizes borrowers into healthy or high-risk loan statuses without significant bias or a high rate of false positives or negatives. The decision matrix is based on variables such as borrower debt, number of accounts, number of derogatory marks, total debt, and borrower income.

Variables to Predict
=
Borrowers are classified into one of two loan statuses: Healthy Loan (0) or High-Risk Loan (1). Those categorized as Healthy Loans may be subject to less scrutiny from the lender compared to those classified as High-Risk Loans.


Machine Learning and Methodology
=
In order to determine the accuracy of this decision matrix, I imported a lending_data CSV and converted it to a Pandas DataFrame. I then named the dependent variable loan_status (the loan classification as healthy or high risk) and all other variables or columns from the DataFrame as the independent variables (context used to determine if a loan is healthy or high risk). I used the LogisticRegression function from sklearn to create a model trained from a random selection of the lending data that predicts which category a borrower is likely to fall into based on the independent variables. I then compared the predicted outcomes to the actual tested outcomes for loan status using a confusion matrix and classification report. Based on the matrix and report, I found the following results:



## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.


* Machine Learning Model 1: LinearRegression
    * This linear model is even less reliable than the logistic model. However, these results are weighted due to the large difference in the number of borrowers who were classified into the healthy and high-risk loan statuses. This data isn't shown as separate accounts displaying the accuracy for borrowers sorted into each loan status individually, so it is difficult to analyze the decision matrix between each status separately. However, when considered together, the linear regression model is a moderately good predictor of loan status.

Looking at the R-squared value, which is essentially an indicator of accuracy ranging from 0 (very low accuracy) to 1 (exactly accurate), we find a value of 0.78. In our case, the R-squared value is roughly aligned with the tested data points. However, there is still a large amount of variance between the data and the predictor, meaning there is a lot of room for false negatives and false positives using the linear model..
    
    

* Machine Learning Model 2: LogisticRegression
    * For borrowers sorted into the Healthy Loan Status of 0 was extremely accurate. The precision and recall reports were both 1, meaning this method detects ALL or NEARLY ALL the borrowers with the given variables and correctly predicts the outcome of a healthy loan extremely accurately. The model correctly identifies all healthy loans (true positives) and doesn't make any mistakes in either direction (false positives or false negatives).
    
    * For borrowers sorted into the High Risk Loan Status of 1 was moderatly accurate. Since the recall is 89% and it is only precise for only 87% of the data points, this logistic model can be used to make predictors for high risk loan status, but should be used with caution since there is room for error. Given the 11% false negative rate, there is a risk of underestimating the number of high-risk loans, which could lead to inadequate risk assessment and potential financial losses. Similarly, the 13% false positive rate may result in unnecessary scrutiny or denial of loans to borrowers who are not actually high-risk.

## Summary
* Out of the two models, the logistic model is more preferred. It is more precise than the linear model in using predicted values to determine the loan status of a borrower, both for high-risk and healthy loans. The accuracy for healthy loans is extremely precise. However, it should be noted that there is more room for false positives with high-risk borrowers. This may result in additional scrutiny of borrowers who are incorrectly categorized as high-risk. Nevertheless, having more false positives is preferable to the alternative: false negatives. False negatives would result in less scrutiny of borrowers who have the potential to cause significant financial loss to the lender. Overall, it is better to spend more resources monitoring loans that may not need it than to risk a loss of money by failing to direct resources to the high-risk loans that do need it, which could lead to significant financial losses.

* TLDR; Lostistic Model is both more accuarte than Linear Model and preffered when analyzing the types of risk due to false positive potential
