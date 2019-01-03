## Problem Statement

**Obtain the data using API and perform Natural Language Process (NLP) combine with machine learning methods to analyze and classify posts from two different subreddits.**
    
    
## Executive Summary

Reddit is an American social news aggregation, web content rating, and discussion website founded by Steven Huffman and Alexis Ohanian in 2005. Registered members submit content to the site such as links, text posts, and images which are organized by subject into user-created boards called "subreddits". Since there are many subreddits covering a variety of topics including news, science, movies, music, and image-sharing, creating a system that could classify posts into each different subreddits might be helpful in the future. In order to demonstrate the filtering system, I obtained the data (title and text) from republican and democrat subreddit and created a classifying model using natural language processing combining with machine learning algorithms. 

## Data Dictionary

**Used Python Reddit API Wrapper (PRAW)**
- Obtain API keys from [Reddit Developed Applications](https://www.reddit.com/prefs/apps/)
    - Client id
    - Client secret
    - Password
    - User agent
    - Username

**Obtain Two datasets**
- rep.csv
- dem.csv

|Feature|Type|Description|
|---|---|---|
|Label|object|Label of the subreddit (Rupublican/Democrat)| 
|Title|object|Title of the post| 
|Text|object|Texts of the each post| 

## Method

- Obtain the data from Reddit
- Check and clean the data
- Use NLP to create features
- Build models
- Select the best model
- Interpret the model


## Conclusion

**Best Model**
- Logistic Regression
    - Penalty = 'l1'
    - C = 1
- Tf-idf Vectorizer
    - stop words = english
    - max feature = 248
    - ngram range = (1,2)
    - min df = 3

**Train Accuracy = 0.767**

**Test Accuracy = 0.748**

## Recommendation

**Interpretation**
- Top words to predict republican subreddit post (high positive coefficient)
    - kavanaugh
    - climate change
    - gun

- Top words to predict democrat subreddit post (high negative coefficient)
    - hillary
    - women
    - election

**Misclassification**
- Some post can come from both sides (neutral)
    - *Finland, Denmark, Germany halt arms sales to Saudi Arabia*
    - *Hillary Clinton will run for president again in 2020, former adviser says*
- Titles with one or two words (useless posts)
    - *Journalism...*
    - *So True*

**Recommendation**
- Create 3 classes (Democrat = 0, Republican = 1, Neutral/useless = 2)
- More data (posts with texts)
