# Sentiment Analysis on Tweets about ChatGPT
> After ChatGPT was launched, many X (formerly twitter) users shared their excitemnt, experiments and opinions on Artificial Intelligence.
Many Companies use 'Sentiment Analysis' as a tool for analysing peoples opinion on their product and look for keywords in improving their product.
In this case, tweets about ChatGPT been analysed for gaining insight in to the people's feelings and sentiments on ChatGPT.
![Word Cloud of dataset](https://github.com/KuntamukkalaPavanKumar/code_clause_sentiment_analysis/blob/main/wordcloud.png)


## Table of Contents
* [Dataset](#data-set)
* [Procedure](#procedure)
* [Conclusions](#conclusions)


## Data-Set
- The Data is openly avaialable on kaggle website (https://www.kaggle.com/datasets/charunisa/chatgpt-sentiment-analysis)
- The data consists of a .csv file containing 3 columns 'Unnamed', 'tweets', 'labels'.
- The tweets are categorized in to three categories:
    - good
    - bad
    - neutral
- During Encoding process:
    - The 'good' category is given a number 2
    - The 'neutral' category is given a number 1
    - The 'bad' category is given a number 0

## Procedure:
1. Loading Dataset:
    - The dataset contains approximately 50% tweets classified as 'bad', 25% of them as 'bad', 25% as 'neutral'.
![distribution_data](https://github.com/KuntamukkalaPavanKumar/code_clause_sentiment_analysis/blob/main/tweetsdistribution.png) 
2. Data Cleaning:
- This involved following steps:
    - Most of the tweets were filled with emoticons, emojis etc.,
    - Those were removed from 'tweets' column.
    - The alphabets in the tweets are converted to lower case.
    - Many tweets were filled with website links which redirect them to ChatGPT page. Those links follow a format of https:// or http://
    - The tweets which follows the above pattern are completely substituted by white space.
    - The tweets containing special characters, new line characters are also substituted by white space.
    - The tweets is broken down to word tokens used word_tokenize function
    - Then WordNetLemmatizer() is used to lemmatize the word tokens. Since using StemPorter or SnowballPorter are not properly converting words to their root form.
3. Sentiment Analysis:
    - Word Clouds:
        - 'Good' tweets contained words such as 'amazing', 'answer', 'interesting', 'better', 'love', 'fun' etc.,
        - 'Bad' tweets contained words such as 'stackoverflow', 'google', 'search', 'time', 'future', 'midjourney', 'chatbot' etc.,
        - 'Neutral' tweets contained words such as 'tech', 'idea', 'find job', 'google', 'content', 'read', 'work' etc.,
    - Subjectivity vs Polarity:
![subjectivitypolarity](https://github.com/KuntamukkalaPavanKumar/code_clause_sentiment_analysis/blob/main/subjectivityvspolarity.png)
        - Subjectivity > 0.5 indicates the text contains more personal opinions and feelings.
        - Subjectivity <0.1 indicates the text contains objective words and little to no personal opinions.
        - Positive Polarity score indicates 'positive sentiment'
        - Negative Polarity score indicates 'negative sentiment'
        - Zero Polarity score indicates 'Neutral'
    - In our case, as the subjectivity score increased to 1, the polarity score became so diverse ranging from -1 to +1.
    - This indicates that as subjectivity score is increasing, the feelings or personal opinions in tweets also increased. But they contain both positive sentiments and negative sentiments.
    - This might be due to misclassification of some of the tweets as 'bad'.
- Train Test Splitting Data
- Under Sampling Training Data:
    - To avoid biasness in the model, Undersampling been chosen to undersample the data. Since the data is dominated by 'bad' category tweets.
    - This undersampling is performed only Training dataset not on test dataset.
- TFIDF Vectorizing the train and test data:
    - Only Train data is fitted and transformed using TfidfVectorizer()
    - The Test data is only transformeed using TfidfVectorizer()
- Model Building:
![models](https://github.com/KuntamukkalaPavanKumar/code_clause_sentiment_analysis/blob/main/accuracyscoremodels.png)
    - Logistic Regression:
        - An accuracy score of 83% is acheived in classfying the tweets as good, bad or neutral
    - Decision Tree Classifier:
        - An accuracy score of 75% is acheived in classifying the tweets as good, bad or neutral
    - Random Forest
        - An accuracy score of 65% is acheived in classifying the tweets as good, bad or neutral.

## Conclusions:
1. Logistic Regression model gives better performance over other models in terms of accuracy.

## Contact
Created by [@KuntamukkalaPavanKumar] - feel free to contact me!
