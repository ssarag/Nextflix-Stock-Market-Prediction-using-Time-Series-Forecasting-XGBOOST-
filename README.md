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

In time series analysis and forecasting, “time” can be the only feature you have at your disposal so it’s better to extract as much information as possible from it. The following function creates columns out of the DateTime index.

For example, at the time 1/1/2017 0:10 , the command df.index.hour will extract the value 0, since it’s midnight. df.index.dayofweek will show a 6 as January 1st, 2017 was a Sunday (numeration starts from 0), and so on.

by running the function create_features on our df, we instantly create all the features defined in the function.

![image](https://user-images.githubusercontent.com/103538049/211171627-b692666e-75dc-438a-9fe6-865b6fce81d5.png)



