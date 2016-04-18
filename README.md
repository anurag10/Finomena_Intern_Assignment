# Requirements: 
1. Device should be installed with IPython Jupiter Notebook and Anaconda to run the .ipynb file. 
2. Ensure that you have dataset downloaded from  https://www.kaggle.com/c/bnp-paribas-cardif-claims-management/data
3. Keep the extracted csv files in the same folder where the program is stored. And DO NOT RENAME those files.
4. sample_submission.csv is the file which gives the predictions of test data.

# Steps to run the program.

1. open jupiter notebook.
2. load the trainnig data set named "train.csv".
3. run each cell orderly one by one.
4. After training of the model is complete, load "test.csv".
5. Predict its output using above model. Just keep running each cell in the program orderwise.
6. Open "sample_submission.csv" to view your predicted output.

# Approach:

The problem is to predict whether a claim will be expedited for faster payment or not. An anonymized data on 131 variables that are either numeric or categorical is given. It seems that these are answers to an intake interview questionnaire. It is also likely certain questions ask respondents to skip over sections, since many individuals have missing values for many of the variables, and certain categorical variables appear to be very good at predicting the degree of “missingness” for a claim.


Thought of dropping those rows having less than 30 columns filled. But realised that it can lead to a loss of information. Missing values for many columns are informative. So filled categorical NaN values with 0 and for continous variables, I used mean to fill NaN values. 
On observing missing data, it turns out that there is a pattern to the missing data–if you are missing data on one variable, then it is highly likely to be missing a lots of data on many variables, and it’s possible that this will be highly predictive of whether a claim is expedited or not. 

On v3, "missing data" makes a claim more likely to be expedited, and on v71, "missing data" makes a claim much less likely to be expedited. And on v52, having "missing data" will lead pretty strongly to an expedited claim.

Observed relationship between different variables using scatter plots and histogram. Key findings were:
Following pairs of variables are correlated: 
1. v17 & v76
2. v115 & v69
3.v58 & v100
4. v47 & v110
5. v91 & v107  


Tried to fit SVM Model. But because of the size of data it was taking too much time. Ran Logistic Regression also but it gave poor result. So then moved to Decision Trees as they perform well on large datasets and categorical variables.

 