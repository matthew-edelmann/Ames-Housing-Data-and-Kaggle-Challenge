# Project 2 - Ames Housing Data and Kaggle Challenge
## by: Matthew Edelmann

### Overview

This is an overview of my project. 

### Problem Statement

We want to create a good model for determining the home price given a set of training and testing data.

### Datasets

We use 2 data sets. One home training data set. The other is the home testing data set. We will train our data on the home train dataset. We will test it on the other data set.

* [`train.csv`](./data/train.csv): Home training data set

* [`test.csv`](./data/test.csv): Home testing data set

The data dictionary telling what our columns are is here:
http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

### Deliverables

In both data sets, we have the same sets of columns except for one. The one is the sales price. We have this on the train set but not the test set. This is because we are trying to find the sales price of the test set using our model prediction. These columns cover a range of data which can be found in our data dictionary. First and formost we checked the list of of null values. We want to know how many null values are in each columns. We decided that columns with null values over 50. For columns that have null values between 1 and 50 we simply drop the null rows.

Looking at this list we see that there are many columns that are far too similar to each other. So we deleted near duplicate columns from each list. The columns we chose to delete are:

    ['MS SubClass', 
    'Lot Shape', 
    'Lot Config', 
    'Land Slope', 
    'Condition 2', 
    'House Style',
    'Overall Cond',
    'Year Remod/Add',
    'Exterior 2nd',
    'Exter Cond',
    'BsmtFin SF 1',
    'BsmtFin SF 2',
    'Bsmt Unf SF',
    'Bsmt Full Bath',
    'Bsmt Half Bath',
    'Heating',
    'Garage Cars']
 
 The last bit of cleaning that I did was to convert the 'Yes' and 'No' rows in the 'Central Air' column into 1's and 0's respectively. With that the data was cleaned. 
 
 Next I looked at the correlation between salesprice and the non object columns and only kept those which the absolute values of the correlation was at least 0.6. Then I made dummies of the object columns. Again, looking at this correlation, I only kept the columns which the absolute values of the correlation was at least 0.6. So the columns we ended up with in the end for our X set were:
 
     ['Overall Qual', 
     'Gr Liv Area', 
     'Garage Area', 
     'Total Bsmt SF', 
     '1st Flr SF', 
     'Exter Qual_TA']
     
Of course our y set was SalesPrice. Then we ran our train test split and created a linear regression model. But before we did this, we created a 2 degree polynomial of these columns. This means that we look at all the columns and their values, as well as each column multiplied by each other column (and thereselves). From this we got our predictions for the SalesPrice for the test.csv data. 

I tried to improve the model with and OLS model, a lasso model, and Elastic Net model, but none of these were succesful in improving the model.

 ### Conclusion
 
 The model gave us These R2 scores:
 
Training R2: 0.8589933055335499
Testing R2: 0.879607496219049

And this cross validation score:
0.8219401785265875

That means the model was only slightly underfit and it explains about 82% of the data.
 
 ### Potention further findings
 
 Given more time, I would try other columns as well as trying to get the OLS model, a lasso model, and Elastic Net model to work.
 
 
 
 
 