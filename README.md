# Nextflix Stock Market Prediction using Time Series Forecasting (XGBOOST)

The project's goal is to leverage time series analysis to predict stock market price of Netflix. 

# Data
Many academics and analysts have found it challenging to master the art of predicting stock values. Indeed, investors are keenly engaged in the field of stock price prediction research. Many investors want to know the stock market's future scenario in order to make a smart and profitable investment. Good and successful stock market prediction systems assist traders, investors, and analysts by giving useful information such as the stock market's future direction.

The dataset is taken from Kaggel - Netflix Stock Price Prediction.The Dataset contains data for 5 years(5th Feb 2018 to 5th Feb 2022).
Some of the features in the data are:

1. Date - Everyday price
2. Open - Price at which stock opens
3. High - Today's High
4. Low - Today's low
5. Close - Close price adjusted for splits
6. Adj Close - Adjusted close price adjusted for splits and dividend and/or capital gain distributions.
7. Volume - Volume of stocks. 


# Importing Dataset
The very first step of virtually every data science project is importing the dataset we’ll be working with along with the libraries needed for the first sections.

The libraries needed for the data import and EDA portions of the project are certainly Pandas and NumPy, along with Matplotlib and Seaborn.

![image](https://user-images.githubusercontent.com/103538049/211171335-0f87beac-042c-463f-a587-95cd3bee5700.png)


We can see that each feature presents only numerical values, we can therefore assume that a potential prediction task will need regression techniques and not classification. As the dataset’s index is in numbers, I used the DateTime column as my index, it’s going to be easier for the chart plotting. 

# Exploratory Data Analysis

We can now focus on data exploration and visualization.

I started by plotting a correlation matrix using seaborn. The correlation matrix shows us the single correlation between each feature and the others on the dataset. In general, the correlation can be:

<0.3 and therefore weak
between 0.3 and 0.6 and therefore moderate
between 0.6 and 0.9 and therefore strong
>0.9 extremely strong
>
The sign, on the other hand, indicates whether the two factors grow in the same direction or in the opposite one. A correlation of -0.9 indicates that as one variable increases the other decreases. Depending on the uncertainty of the environment though, the ranges can change. In quantitative finance, a 0.3 or 0.4 correlation can be considered strong.

![image](https://user-images.githubusercontent.com/103538049/211171476-85a136fa-01e0-45fa-b005-55517329f24b.png)

Observations from the heatmap:

Open, High, Close, Adj Close, Low, are strongly correlated to all each others. 

Volume shows a weak correlation with others. 

# Feature Creation

In time series analysis and forecasting, “time” can be the only feature you have at your disposal so it’s better to extract as much information as possible from it. The following function creates columns out of the DateTime index. For example, at the time 1/1/2017 0:10 , the command df.index.hour will extract the value 0, since it’s midnight. df.index.dayofweek will show a 6 as January 1st, 2017 was a Sunday (numeration starts from 0), and so on.
By running the function create_features on our df, we instantly create all the features defined in the function.

![image](https://user-images.githubusercontent.com/103538049/211171627-b692666e-75dc-438a-9fe6-865b6fce81d5.png)

# Box plots of the features to represent trends 

![image](https://user-images.githubusercontent.com/103538049/211171717-1b31d75c-9ce8-4a6f-bfde-dae9b10b6843.png)



![image](https://user-images.githubusercontent.com/103538049/211171815-b147ac32-91ee-4591-b7f0-11803c06bf91.png)



![image](https://user-images.githubusercontent.com/103538049/211171819-1ffabdb9-4c41-4b71-b56c-53ab94dc7a3b.png)


![image](https://user-images.githubusercontent.com/103538049/211171845-cbc1c304-07f4-44b5-ac65-cba2acf4de5d.png)


# Train Test Split

At this stage, the dataset can be split between training and testing. In a normal scenario, we would randomly select new records to train the algorithm and test it on the remaining ones. In this case, it’s important to preserve a time sequence between the training and testing records. Therefore 70 percent of data from 2018-02-01 to 2021-06-01 is in the traning dataset and the data from 2021-06-01 to 2022-02-01 is in the testing set. 

![image](https://user-images.githubusercontent.com/103538049/211172437-2e31cd43-f7fa-4132-aa59-fbd4d3739452.png)


# Predictions

To predict records in our test set I have used Gradient Bossting (XGBOOST) algorithm. 

Hyperparameters settings for the algorithm is as follows:


n_estimators : the number of learning rounds the XGBoost algorithm will try to learn from the training data

max_depth : the maximum depth a tree can have, a deeper tree is more likely to cause overfitting

learning_rate : or shrinkage factor, as new trees are created to correct residual errors, the learning rate (<1.0) “slows down” the ability of the model to fit the data and consequently learn as the number of trees increases

verbose : how often the model prints out on the console the result, we set 100 here as the n_estimators is quite high. The default value is 1


# Output of the forecasting

![image](https://user-images.githubusercontent.com/103538049/211172595-db641550-1650-48e3-832f-eafee9dc2578.png)






