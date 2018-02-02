# r_crypto_sentiment

Got a trading idea to backtest and further investigate. The idea is to find altcoins that are potentially gaining market cap significantly in short coming future. For example, from top 100 to top 20 in terms of market cap. The price movements are largely driven by credible news or FUD marketing.

1. Download a list of coin identifiers from coinmarketcap.
2. Do a social media sentiment analysis on coins.
3. Join the sentiment data with coin price data to see if it proves to be opportunistic.

## Set up twitter sentiment analysis in R

I'm following [this guide by Sergey Bryl'](https://analyzecore.com/2017/02/08/twitter-sentiment-analysis-doc2vec/) using doc2vec.

The training data set used by Sergey, including 1.6 million classified tweets, can be found [here](https://docs.google.com/file/d/0B04GJPshIjmPRnZManQwWEdTZjg/edit). I've extracted them into the sub folder ```trainingandtestdata```.

```model_training.R``` can be used to train the sentiment analysis model. The same script would save the trained model as file ```glmnet_classifier.RDS```. So you don't really need to download the above mentioned training dataset.

## Apply the trained model to an example cryptocurrency

The code example ```twitter_sentiment_example.R``` is for getting the tweets and predicting the probability of sentiment positiveness. ```twitter_sentiment_visualisation.R``` uses ggplot to visualise the sentiment movement over time. The example result plot of IOTA sentiment on 2018-01-27 morning is shown below.

![IOTA sentiment on 2018-01-27 morning](/results/IOTA_sentiment_2018-01-27.png)

## Issues encountered

The free twitter search API doesn't return tweets older than 7 days. There are other request limitations when using the API. It is therefore pretty expensive to get historical datasets to join with the historical price data.

It might be possible to get a sentiment LIVE view on multiple cryptos.

[https://crypto-sentiment.com/](https://crypto-sentiment.com/) has three useful sentiment analysis charts.
