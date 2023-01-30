
![twitter-api-sign-up](https://user-images.githubusercontent.com/31993566/215386277-dba32683-d6bf-4dbf-98b0-e6e59555e122.png)


**UNDERSTANDING TWEEPY AND HOW IT WORKS**

**Introduction**

- Tweepy is a popular Python library used for accessing the Twitter API. 

- In order to extract a large number of tweets, Tweepy provides two classes : **Cursor** and **Paginator**. 

- Both classes help to handle the pagination of tweets when the number of tweets exceeds the standard rate limit.



**Tweepy.Cursor and Tweepy.Paginator**

- Both are part of the Tweepy library and is used to retrieve tweets from the Twitter API in a paginated manner. 

- **"Paginated manner"** means that the results are divided into pages, rather than being returned all at once. This helps to manage large amounts of data and improve performance.



**Difference**

The main difference between the two classes is in how they retrieve the tweets and handle pagination.


**Tweepy.Cursor** 

- Designed to retrieve tweets in a stream-like fashion, making it easy to retrieve large amounts of tweets without having to worry about pagination or rate limiting. 

- The class automatically handles pagination for you, automatically requesting the next page of results each time you iterate over the results. 

- Uses the OAuth (consumer key, consumer secret, access token, and access token secret) to authenticate with the Twitter API.


**Tweepy.Paginator**

- Designed to handle pagination manually. This class requires you to specify the number of tweets to retrieve on each page, and provides methods for accessing individual pages of results. 

- This allows you to have more control over the pagination process, and can be useful when you need to retrieve only a specific set of tweets or when you need to process the results in a specific order.

- Uses the bearer token to authenticate with the Twitter API.



In order to retrieve Elon Musk's tweets, the **tweepy.Cursor** class is used to retrieve tweets from a Elon Musk's timeline.

      for tweet in tweepy.Cursor(api.user_timeline, screen_name=user, tweet_mode='extended', exclude_replies=True, ).items():


**Parameters** 
 
 - **api.user_timeline** : retrieve tweets from the timeline of a user specified by the screen_name parameter.
 
 - **tweet_mode='extended'** : retrieve the **full text** of the tweets, even if the tweets are longer than 140 characters.
 
 - **exclude_replies=True** : exclude **replies** from the timeline, so that only original tweets are retrieved.
 
 - **.items()** : iterate over the tweets in the timeline.
 

**Note**
Each tweet retrieved includes a **tweet ID**, which is a **unique identifier** assigned by Twitter to each tweet. 
Those tweets collected that are without the keywords are filtered out. 


Next, the **tweepy.Paginator** class is used to retrieve **quoted tweets** for each tweet id collected. 

    for tweet in tweepy.Paginator(client.get_quote_tweets, id = tweet.id, max_results=25, exclude='retweets').flatten(limit=25):


**Parameters**

 - **client.get_quote_tweets** : a method or function provided by the client object that is used to retrieve quoted tweets from the Twitter API.
 
 - **id** : the ID attribute of the Status object representing the tweet from which we retrieved the quoted tweets. The value for this parameter is obtained from the tweet.id property of the tweet object.

 - **max_results** : specifies 25 quoted tweets that the API should return in a single request. 

 - **exclude** : specifies any tweets that are retweets should be excluded from the response. 
 
 - **limit** : used by the flatten method and specifies the 25 tweets to be returned.  
