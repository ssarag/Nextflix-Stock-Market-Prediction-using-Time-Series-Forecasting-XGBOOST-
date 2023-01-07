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


