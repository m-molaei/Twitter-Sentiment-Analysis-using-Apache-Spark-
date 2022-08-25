# Twitter-Sentiment-Analysis-using-Apache-Spark-
Sentiment analysis using deep learning models and FastText embedding on Apache Spark
I implemented a sentiment analysis model on Twitter using Apache Spark. I used FastText embeddings and deep learning RNN models (LSTM, GRU, and CNN) with Analytics Zoo library. Also, this work included a pre-processing framework based on Dataframe that performs much better than RDD-based architectures in terms of processing time and volume of data that can be processed.
In addition, I used MongoDB and Apache Cassandra as this model's databases and compared them to the Apache Spark file storing and retrieving system.

We also published an article for introducing a Dataframe based pre-processing framework that you can get from here:
https://jad.shahroodut.ac.ir/article_2394.html

I hope this will be useful for you ;)

## Code Explanation

1. Importing libraries (Probably you will need to install some of them such as Analytics-Zoo and findspark)
2. Initialize Apache spark cluster
3. Import and reading sentiemnt140 dataset with pandas. (You will need to change dataset's path.)

    Authentication operations were completed with Tweepy module of Python. You must take keys from Twitter API.
    StreamListener named TweetListener was create for Twitter Streaming. StreamListener produces data for Kafka Topic named 'twitter'.
    StreamListener also calculates Tweets' sentiment value with AFINN module and sends this value to 'twitter' topic.
    Producing data was filtered about including desired topic.
    Kafka Consumer that consumes data from 'twitter' topic was created.
    Also, it converts streaming data to structured data. This structured data is placed into a SQL table named 'data'.
    Data table has 2 columns named 'text' and 'senti_val'.
    Average of sentiment values of senti_val column is calculated by pyspark.sql.functions.
    Also, user defined function named fun is created for status column.
    Status column has POSITIVE, NEUTRAL or NEGATIVE that change according to avg(senti_val) column in real-time.

