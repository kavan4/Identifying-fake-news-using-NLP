# Using NLP to identify Fake News headlines using reddit submissions


### Contents:
- [Problem Statement](#Problem-Statement)
- [Executive Summary](#Executive-Summary)
- [Data Dictionary](#Data-Dictionary)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

## Problem Statement

The project is led by Toronto Analytica, think tank based in Toronto. Fake News is an ever growing problem in this age of technology and social media. The effects are varied and well documented. The aim of this project is to identify articles that are Fake News articles using machine learning and Natural Language Processing (NLP) techniques.

At its essence, this is a binary classification problem consisting of posts from two Subreddits, _r/TheOnion_ which represent Fake News articles and _r/Politics_ which represent real news articles.

_r/TheOnion_ and _r/Politics_ were chosen because the contents of both posts can be very similar. There are overlapping topics and we can see if the accuracy of the classification is indeed going to be good or bad.

A few machine learning models will be going through supervised learning to be trained on existing data from each Subreddit. The model with the best accuracy will be the model of choice for this classification problem. This model can continue to train on new data for new posts to enhance its accuracy.

## Executive Summary

In recent years, there has been an increasing number of Fake News articles that are shared among people. At its best, it leads to misinformed people and at it worse it has been documented to lead to massacres. Understanding the texts through NLP of two subreddits _r/TheOnion_ and _r/Politics_ are good starting points for a classification task.

Data is gathered by scrapping posts from the two popular subreddits and then training the model on 75% of the data and subsequently the other 25% as the unseen test set to evaluate the model performance. The models used will be:
- Logistic Regression
- Multinomial Naive-Bayes Classifier
- Gaussian Naive-Bayes Classifier
- Decision Tree Classifier
- Bagging Classifier
- K Nearest Neighbours Classifier
- Random Forest Classifier
- Extra Trees Classifier
- Support Vector Classifier

After the training and testing phases, Logistic Regression and SVC performed the best in terms of the accuracy score.

## Data Dictionary

| Field     | Type   | Description                                                         |
|-----------|--------|---------------------------------------------------------------------|
| clean_title_txt | string | The  title and selftext of reddit post                               |
| target     | int    | target = 1 refers to r/TheOnion, target = 0 refers to r/Politics |

## Conclusions and Recommendations

### Model Comparison

| Model               | Training Score | Test Score | ROC AUC Score |
|---------------------|----------------|------------|---------------|
|Logistic Regression|0.9845|0.8407|0.9119|
|SVC|0.9963|0.8407|0.9178|


In terms of test score, Logistic Regression and SVC modeles performed the best at 0.8407. SVC was ultimately the better one with a relatively higher ROC AUC score of 0.9178.

### Recommendations

The model ignores all images, emojis, or any other non alphanumeric character. Any information conveyed that way would be ignored.
The model does not look at the context of the word so instances where OP writes something but means something else would not be captured (e.g. - sarcasm)

Refining stop words to reflect popular words used in each subreddit will help increase performance.

Sentiment analysis would be interesting to explore and help improve the model.

Regularization can be added to further improve performance. - added regularization to logistic regression. unfortunately performance increase was not significant.

At this point some form of feature engineering would be required since various models with different transformers, regularization, and hyperparameter tuning have been tried.

Manually adding stopwords to remove some of the more frequent words that appear between both the subreddits might be useful next step.

Also, manually going through the misclassifed entries will be helpful to gain insight into where the model falters.

Additionally, more features like length of posts can be identified and input into the model to see if it will increase accuracy scores.
