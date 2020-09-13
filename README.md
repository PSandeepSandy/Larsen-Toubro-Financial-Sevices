# Larsen-Toubro-Financial-Sevices

This is a binary classification problem where participants were supposed to predict whether a particular borrower would default in his first month of EMI payment.

### To view it on Kaggle
https://www.kaggle.com/sandeeppat/ltfs-top-3-5-kernel

### Rank - 47th (out of 1352 teams). Placed in the Top 3.5% .

## Approach
### FEATURE ENGINEERING -

- Anomalous Branch - Keeps track of the branches, from where, certain loans have been sanctioned and then the buy has been done at a showroom which is far from that bank,possibly even in a different state or city. This is tracked by seeing the usual showrooms from where buys take place if a loan is sanctioned from a particular branch. Certain anomalies detected in this list have been tracked in this feature.
- The super-messy Perform_CNS Score categorical data have been re-binned to give a cleaner idea of the CIBIL scores. There have been 2 new binnings made. One on the basis of some background knowledge about banking, and the way banks segregate the users and the second according to the data provided in the dataset.
- The number of ID Proofs a person has submitted at the time of taking the loan - Assumption being, the more number of IDs shown, the more the credibility of the borrower.
- The number of Primary and Secondary accounts a person already has defaulted, overall as well as over the last 6 months.
- The borrower's age, his/her average account age,i.e, on an average how much time he/she takes to give back all the lent money.
- Whether the borrower is a "Student" or a "Senior Citizen" from the age and the employment status.
- Since the model was suppposed to predict who would be defaulting in the FIRST MONTH of taking loan, so, keeping track of which all users defaulted in the first month only, rather than who all defaulted over-all in the train set makes more sense as the model would then be able to recognize the trends and behaviour more easily.

### MISSING DATA HANDLING -

- The missing "Employment" were treated as "Unemployed" as of that moment.
- The UNEMPLOYED borrowers were categorized into "Students" and "Senior Citizens" taking a hint from their ages.

### STRATIFICATION -

- Stratification done on the basis of similarity between the train and test set, rather than doing on the basis of the classes.

### TRAINING -

- Five-Fold Cross Validation was used and the predictions on the test set were taken over the model trained on each fold and were finally averaged over all the folds to get the final prediction over the test set.
- Heavy Parameter Tuning done on CatBoost Classifier, LightGBM, Random Forest and XGBoost, with CatBoost out-performing the rest. Hence, finally CatBoost was used for submission.
- Stacking was done, with 20 CatBoost models and a meta learner (Logistic Regression) was used.

