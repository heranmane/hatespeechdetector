# hatespeechdetector

Although racism and hate speech have always existed, rapidly expanded access to the internet has turbo-charged the proliferation of racist views. The purpose of this project is to create a model that can keep pace with that proliferation by automatically flagging racism on Twitter. 

To tackle this problem, I turned your request into a question - “What would a tool that can identify racism on Twitter look like?” This required me to: 
•	Define racism:  set parameters that would capture racist sentiments in tweets; 
•	Find data: identify data sources that provide ample examples of racist and non-racist tweets; 
•	Create the model: clean the dataset, write code capable of reading the data and learning how to identify expressions of racism within the dataset; 
•	Identify limitations: review data produced by the model for its limitations; and
•	Next steps: describe next steps to overcome the limitations of the model.

To identify examples of racism on Twitter, I looked for common forms of hate speech as expressions of racist views. I won’t reproduce examples here, but they are available for your review in the model. I then sought to locate usable data sets. 
 
My initial search for data sources returned several options, each with strengths and weaknesses. I selected Kaggle’s collection because it provided the data in the most ready-to-use format. The other options offered greater specificity or more tweets but did not readily lend themselves to the rapid analysis required for this short-term project. I collected the Kaggle data, which contains more than 30,000 tweets organized into three columns consisting of ID, Label, and Tweet. 

It is also important to note here that the Kaggle Labels are “hate detected” or “no hate detected”. Hate speech is very broad and could be attributed to various types of “offensive” language that do not necessarily register as racist, such as sexist, homophobic, antisemitic, or simply unpleasant language. A fully effective tool would require a more sophisticated labelling system to distinguish between types of hate speech, but the binary of “hate detected” or “no hate detected” is adequate for the purposes of this model.

A review of the structured Kaggle data showed that only 2,242 out of the 31,963 tweets were labeled as “hate detected,” which heavily skewed the dataset toward irrelevant content. This imbalance would have prevented the algorithm from learning how to identify hate speech. To streamline the algorithm training, I shrunk the dataset to 4,927 tweets without eliminating any of the tweets labeled as “hate detected”. 

It was necessary to further prepare the data to create a training dataset. I used Bag of Words and the Term Frequency Inverse Document Frequency methods, which prioritized words relevant to the model and I also eliminated punctuation, symbols, and hashtags from the structured Kaggle data. 

The training dataset is then split: 80% training data and 20% test data. I used this validation set to evaluate the model and to finetune the model’s hyperparameters. Then using Naïve Base Classifier, I classified  tweets as “hate detected” or “no hate detected”.  
 
After running the model on the training data, I tested it with examples of racism on Twitter, ensuring that the model could accurately classify the example tweets. Then, I used the model on a dataset of Tweets that I scraped directly using Twitter API. I programmed the scrape to convert the data into a CSV file that automatically ingests itself into the model for analysis. 

Although the model is capable of picking up on explicitly offensive words and tweets, it is limited in its ability to classify hate speech. Natural Language Processing models are useful for processing speech and conducting sentiment analysis, but they are deficient when it comes to contextualizing and/or understanding intent of the text/speech. For example, the model sometimes classifies references to Black Lives Matter as hate speech, regardless of whether the tweet expresses any racist sentiment.

In order for the model to reach its potential, it must lean more heavily on human understanding. Human beings are typically better equipped to understand the intent of a given tweet and correctly classify it often with a tweet in response. 

Honing the model to collect replies in addition to tweets could vastly improve the model as a tool to flag racism on Twitter. If someone writes something that Twitter users consider racist, those Twitter users will likely call out the Tweet as racist in their replies. Hard coding comments like "this is racist", "you are racist", etc. to the model could help point out posts that are intentionally racist.  Being able to combine the capabilities of machine learning processing with human instinct and intellect would likely create a more accurate model. 


Data Source: https://www.kaggle.com/chirag19/twitter-sentiment-analysis?select=train_E6oV3lV.csv