# Propaganda Detection

(courtesy [Data Science Society](https://www.datasciencesociety.net))

Propaganda is the new weapon which influences people's opinions or beliefs about a certain ideology, whether that ideology is right or wrong. Early identification of propaganda is crucial to start fighting the manipulation spread in news and test hypothesis such as which news sources are biased and propagandistic. It will also benefit the individual user who will be able to check the integrity of news sources.

## Data Source

The training data consists of about 60k news articles, annotated as either “propagandistic” or “non-propagandistic.” The annotation was done indirectly using a technique known as distant supervision, i.e., an article is considered propagandistic if it comes from a news outlet that has been labeled as propagandistic by human annotators. For example, all articles from http://Inexistent-Site-Supporting-Brexit.co.uk would be labeled as propagandistic, even though some of them may not be such, which could potentially introduce noise in the dataset. It has been argued elsewhere that models can deal with such noise if the training data is large enough.

The input data will be presented as one big tab-separated file, where;
* Each line of the file corresponds to a single article.
* Each new line (carriage return) in the original article is converted to two spaces.
* Besides the full text of the article (first column), each line has two additional TAB-separated columns, the unique article id and its gold label, which could be “propaganda” or “non-propaganda”.

[Data Source](https://s3.us-east-2.amazonaws.com/propaganda-datathon/dataset/datasets-v5.zip)

## Overview of Analysis

### EDA (EDA.ipynb)

* Visualisation of class imbalance
* Visualisations of number of words in news with propaganda vs without propaganda
* Collocations, long words analysis and frequency word clouds of both news with propaganda and without propaganda 
* Analysis of different tokenisation methods

### Machine Learning Exploration (ml-exploration.ipynb)

* Generating VADER Sentiment features;
  * VADER is a lexicon and rule-based sentiment analysis tool that is specifically attuned to sentiments expressed in social media, and works well on texts from other domains.
  * As VADER is attuned to social media based text, it does not make sense to use it at word or article level.
  * Hence, each article is split into sentences and the features calculated are: Min, Max and Median sentence sentiment scores for Negative, Positive and Neutral sentiment
* Algorithms tried include:
  * Logistic Regression
  * Naive Bayes
  * SVM
  * Decision Tree
  * Random Forest
  * AdaBoost
* Hyperparameter tuning for Random Forest and Decision Tree (hand-tuning and Random Search)


### Deep Learning Exploration (dl-exploration.ipynb)

* finetuned Glove Word Vectors
* bidirectional LSTMs
* experiments with number of layers
* experiments with additional layers such as Dropout (to prevent overfitting) and BatchNormalisation (to improve optimiser performance)
* Additionally, **dl-sent-exploration.ipynb** combines the Vader Sentiment features with the learned text features



*For model weights please contact me at anusha.lihala@gmail.com*

