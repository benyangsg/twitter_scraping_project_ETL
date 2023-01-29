# Twitter Sentiment Analysis with Database Design and Management.

This project is designed to scrape tweets and quoted tweets from @elonmusk, the official Twitter account of Elon Musk. 

It will perform a sentiment analysis on the latest 20 tweets, providing a summary of the overall sentiment towards the tweets.

Visuals are made for word cloud and show casing correlation between total retweets and likes.

PostgreSQL is the Database Management System of Choice to store scraped and analysed data.

The bot is built using Python in Anaconda and makes use of the following libraries:

#### EXTRACT
* [tweepy](https://www.tweepy.org/) for accessing the Twitter API
* [configparser](https://pypi.org/project/configparser/) for hiding keys and secrets

#### TRANSFORM
* [pandas](https://pandas.pydata.org/) for data manipulation and analysis
* [pytz](https://pypi.org/project/pytz/) for accessing timezone
* [re](https://docs.python.org/3/library/re.html) for cleaning tweets
* [nltk](https://www.nltk.org/) for cleaning stopwords
* [matplotlib](https://matplotlib.org/) for creating visualisations
* [VADER](https://pypi.org/project/vaderSentiment/) for sentiment analysis
* [numpy](https://numpy.org/) support for large, multi-dimensional arrays and matrices

#### LOAD
* [psycopg2](https://www.psycopg.org/) for data migration and manipulation from postgresql

The bot is intended for research and informational purposes only, and it is not affiliated with or endorsed by Elon Musk or Twitter. Use of the bot is subject to Twitter's terms of service and developer agreement.

To use the bot, you will need to have a Twitter developer account and create a new application to obtain the necessary API keys. The bot can be easily modified to target other Twitter accounts or to change the number of tweets analyzed.

### Usage
1. Download the repository
2. Install the necessary dependencies by running conda install in anaconda prompt, refer to requirement.txt for list of dependencies
3. Add your Twitter API keys in the config.ini file
4. Run the scripts in sequence using twitter_bot_everything.ipynb
5. Refer to Workflow and Star Schema diagram below for reference 
6. The analysis of the tweets will be printed in the console
7. The script will output the sentiment analysis result of the latest 20 tweets and quoted tweets of @elonmusk on the console.
