# Twitter-Sentiment-Analysis-using-Apache-Spark
### Sentiment analysis using deep learning models and FastText embeddings on Apache Spark

I implemented a sentiment analysis model on Twitter using Apache Spark. I used FastText embeddings and deep learning RNN models (LSTM, GRU, and CNN) with Analytics Zoo library. Also, this work included a pre-processing framework based on Dataframe that performs much better than RDD-based architectures in terms of processing time and volume of data that can be processed.
In addition, I used MongoDB and Apache Cassandra as this model's databases and compared them to the Apache Spark file storing and retrieving system.

We also published an article for introducing a Dataframe based pre-processing framework that you can get from here:
https://jad.shahroodut.ac.ir/article_2394.html

I hope this will be useful for you ;)

## Code Explanation

1. Importing libraries (Probably you will need to install some of them such as [`Analytics Zoo`](https://analytics-zoo.readthedocs.io/en/latest/doc/UserGuide/python.html) and [`findspark`](https://github.com/minrk/findspark))
2. Initialize Apache spark cluster
3. Import and reading sentiemnt140 dataset with pandas. (You will need to change dataset's path.)
4. Import FastText embeddings with gensim
5. Pre-processing tweets including cleansing, tokening, padding and vectorizing (This step is implemented in two ways: RDD-based and Dataframe-based.)
6. Configuration of Apache Cassandra and MongoDB on Apache Spark
7. Sentiment Analysis models
