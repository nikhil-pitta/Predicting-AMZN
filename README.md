# Using Sentiment Analysis to determine a correlation between Amazon stock prices and product reviews

Presentation: https://docs.google.com/presentation/d/1QZtjymPqnNy_sGf3v1zoxwtoZn7Ocx4IQQDrTLEioZo/edit#slide=id.p

## Abstract
Sentiment Analysis (SA) is a popular ongoing field of research in the text mining industry. It aims to capture opinions and subjectivity from large blobs of text and apply the result to explain real-world phenomena. This project focuses on SA’s usage in explaining and predicting stock prices for Amazon, aiming to identify the hidden association between the product reviews for products specifically made by Amazon and the company’s stock prices in the same period during which the reviews were written. This type of data, in which information is gathered from non-traditional sources, is called alternative data. 

## Introduction
Sentiment Analysis (SA) is the computational study of people’s opinions and emotions toward an entity. Ideally, it is able to discern if a given text has a positive or negative attitude. In this project, we have collected Amazon product reviews spanning from 2016 to 2017 in the hope that the sentiment analysis on these reviews would reveal a hidden association between the attitude of the reviews and the stock prices of Amazon from 2016 to 2017. In the case that there is some sort of correlation, we can adopt a straightforward strategy in which we buy Amazon stock during time periods in which SA indicates that the price will drop, and sell Amazon stock during time periods in which SA indicates that the price will rise. 

## Review of Existing Literature
https://arxiv.org/pdf/1706.00188v1.pdf - Deep Learning for Hate Speech Detection in Tweets
This paper discusses various approaches to using TF-IDF in order to properly perform feature engineering to classify hate speech on Twitter. Moreover, it compares the performance between multiple models when given the same data.

## Dataset
The dataset we used that contained the Amazon product reviews came from Datafiniti, a web scraping service made for reviews. The dataset that contained historical stock price data came from Yahoo Finance; we used the wrapper library yfinance to load the prices.

## Methods
To ensure that product reviews could be processed by our SA model, we first had to determine how to clean the reviews and then stem/lemmatize them. Afterward, we did feature engineering by using term frequency-inverse document frequency (TF-IDF) to figure out the relevancy of a given word used in the product reviews. From our exploratory data analysis, we noted that there was a low amount of negative sentiment reviews, so we performed random oversampling in order to make the class distribution of the dataset more uniform. Finally, we did a train-test split and applied a HuggingFace transformer onto our data, giving us a classifier with around 78% accuracy. To process the historical stock data, we first found the daily average price using the high and low prices. Then, we aggregated these prices by month and calculated each month’s performance by measuring how much the average price of a given month exceeds that on the first day of the month. 

## Results
After plotting Amazon’s stock performance and the average sentiment score for Amazon products for each month, we can see that a weak positive correlation exists. Thus, there exists some type of relationship between the two variables. 

Conclusion
We can see that although the correlation between Amazon product reviews and stock prices is a bit weak, our results indicate that it might be worth looking at product reviews as one possible parameter to estimate appropriate time periods to buy and sell Amazon stock. In the future, we plan to incorporate our results with another existing strategy to see whether it is possible to obtain observable gains. 


