# NLP Analysis of Xenophobic Twitter Comments During COVID Outbreak

## Introduction

Even though COVID-19 has been recognized by many people as past tense, the pandemic has had a profound impact on societies worldwide, affecting every aspect of daily life. Unfortunately, the pandemic has also led to an increase in xenophobic attitudes towards certain groups, particularly Asian and Chinese. Data show that anti-Asian hate crimes increased by 339 percent nationwide from 2020 to 2021 in the United States. In fact, historically, every large-scale outbreak of a pandemic was accompanied by hatred towards a certain ethnic group and the associated violence. 

Social media platforms like Twitter have become a forum for people to express their opinions and emotions about the pandemic and its consequences. In this context, there is a need to understand the nature and extent of xenophobic speech on Twitter during the pandemic. 

Natural language processing (NLP) is a powerful tool that can be used to analyze large volumes of text data and extract meaningful insights from it. In this study, I aim to use NLP techniques to analyze xenophobic Twitter comments during the COVID-19 outbreak. Specifically, I explored the sentiments and themes expressed in these comments, as well as the linguistic characteristics of xenophobic language on Twitter. The findings could help shed light on the prevalence and nature of xenophobia during the pandemic. Understanding why people generate those xenophobic statements and why rumors always spread faster than scientific knowledge can help us better perceive the world and prevent tragedies from happening again.


## Data

In this study, I utilize data from Kaggle.com (You can download the dataset here: https://www.kaggle.com/datasets/rahulgoel1106/xenophobia-on-twitter-during-covid19). 
Kaggle is the world's largest data science community with powerful tools and resources to help achieve data science goals.
The dataset is called "Xenophobia.csv". It contains 43,11477 tweet records of COVID-related statements that people posted between March 6th and May 2nd, 2020.

This is the description of my dataset:
* status_id: A unique id for each tweet [numeric].
* text: tweet text data [string].
* created_at: The timestamp of the tweet [timestamp].
* favourite_count: favorite count of the user of the tweet [numeric].
* retweet_count: retweet count of the tweet [numeric].
* location: location mentioned by the user while tweeting [string].
* followers_count: user's followers' count [numeric].
* friends_count: user's friends' count [numeric].
* statuses_count: user's total statuses count [numeric].

In my analysis, I mainly used records from the text column to conduct my research. 


## Methodology and Output Files

This project requires running two main scripts. The first script (Part One_Xenophobia_Tweets_Sentiment Analysis.py) focuses on sentiment analysis and the second script (Part Two_Xenophobia_Tweets_Topic_Modeling.ipynb) is topic modeling by using Latent Dirichlet Allocation Model. 

In the first script, 'Xenophobia.csv' is mainly used to perform the analysis. My analysis is divided into the following steps:

1. Explore the whole dataset and do a basic sentiment analysis by using TextBLOB. After this step, I obtained the number of positive, negative, and neutral tweets, and plotted a pie chart. 
2. I collect all the tweets that have been identified as negative to form a new dataset and then preprocessed this dataset. Preprocessing steps include:
    * Removing Twitter handles
    * Remove punctuations, numbers, and special characters
    * Lowercase text
    * Remove all words below 3 characters
    * Tokenize the tweets
3. After getting a relatively clean database, I started to identify all tweets that might contain hate speech. The words I used to identify xenophobic speech include:
    ['alien', 'asian', 'kung flu', 'anti-asian', 'china', 'chinese', 'wuhan virus', 'criminal', 'floater', 'foreigner', 'greenhorn', 'aliens', 'foreigners', 'illegal', 'intruder', 'invader', 'migrant', 'invaders', 'immigrants', 'newcomer', 'odd one out, 'outsider', 'outsiders', 'refugee', 'newcomers', 'send her back, 'refugees', 'send him back, 'send them back, 'settler', 'stranger', 'illegal aliens, 'china virus', 'refugee', 'settlers', 'strangers', 'migrants', 'criminals']. 
    There are 52428 xenophobic tweets being found.
4. I redrawn a pie chart of all positive speech, negative speech, neutral speech, and hate speech, and assemble all tweets identified as xenophobic to form a new dataset called 'xenophobic tweets.csv'

In the second script, "xenophobic tweets.csv" is mainly used to perform the analysis, and the analysis is divided into the following steps:

1. Again the data is pre-processed and the steps include:
    * Remove punctuation
    * Tokenization and stop-words removing
    * Use Regular Expressions to remove more random words, like 'aaa'.
2. Data Visualization, including building a wordcloud and examing the length of each tweet
3. Topic Modeling: Prepare the data for the LDA model, run the model, and compute the coherence score

NOTE: Since my version of Anaconda is too old, some code does not run smoothly on Spyder, so I wrote a second script with google collab, and the first script was written with Spyder.

## Results

**Figure 1. Sentiment Analysis**
![plot](https://github.com/Sway367/NLP-Analysis-of-Xenophobic-Twitter-Comments-During-COVID-Outbreak/blob/main/1.%20Sentiment%20Anlysis%20by%20using%20TextBlob.png)

**Figure 2. Percentage of Xenophobic Tweets**
![plot](https://github.com/Sway367/NLP-Analysis-of-Xenophobic-Twitter-Comments-During-COVID-Outbreak/blob/main/2.%20Xenophobic%20Analysis.png)
1.1% of the comments are defined as xenophobic tweets, which has 52,428 tweets. 

**Figure 3. WordCloud of Xenophobic Tweets**
![plot](https://github.com/Sway367/NLP-Analysis-of-Xenophobic-Twitter-Comments-During-COVID-Outbreak/blob/main/3.%20xenophobic_wordcloud.png)

**Figure 4. The Distribution of the length of Xenophobic Tweets**
![plot](https://github.com/Sway367/NLP-Analysis-of-Xenophobic-Twitter-Comments-During-COVID-Outbreak/blob/main/4.%20tweets%20length%20distribution.png)

**Topic Modeling**

* Topic 1: criminal, china, lives, risk, thousands, save, refugees, chinese, covid
* Topic 2: china, covid, world, chinese, virus, people, countries,  don’t, stop
* Topic 3: xenophobic, china, travel, called, trump, racist, illegal, criminal, president, flights
* Topic 4: china, chinese, virus, covid, trump, people, wuhan, cases, calling, criminal
* Topic 5: china, people, covid, chinese, trump, death, dont, migrant, xenophobia, virus

## Limitations and Further Researches

* Different sentiment analysis models yield different results. This analysis didn’t explain why TextBlob is used for analysis but not other models.
* In the sentiment analysis section, the results should be more interesting if we do not only judge the positive and negative of the attitude of comments but also conduct a more in-depth analysis, such as happy, angry, etc.
* There may be some subjective bias in the definition of xenophobic speech. Further exploration is needed to capture more comprehensively all statements about hate.
* The current analysis only focuses on the column ‘text’ ’in the dataset. If I can add time, location (where people's IPs belong), number of followers, and number of retweets in the analysis, the results should be more interesting.
* The results of the current LDA model are far from accurate. We can find better results by hyperparameter testing.
* From a more practical point of view, this is a relatively lagged analysis. This data only shows what people said about COVID during 3 months in 2020. It is not known what impact such rhetoric had on people's attitudes and behavior toward COVID in the following 2-3 years, and how people continue to see Asian hate today. This is a more practical and worthwhile topic to continue to explore.



## Reference

* https://www.kaggle.com/code/christianlillelund/find-hate-towards-asians-in-tweets-svm/notebook
* https://medium.com/towards-data-science/lda-topic-modeling-with-tweets-deff37c0e131



