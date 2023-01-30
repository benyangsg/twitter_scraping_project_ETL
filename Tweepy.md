# Twitter API Application

In order to use Twitter API, a Twitter developer account is required.  Apply for the **Essential** level first, then upgrade to **Elevated** level. 

The steps are as follows:

Go to <https://developer.twitter.com> and sign in to your Twitter account. Navigate to **Products → Twitter API**.

![twitter-api-sign-up](https://user-images.githubusercontent.com/31993566/215386277-dba32683-d6bf-4dbf-98b0-e6e59555e122.png)

Then, scroll down to the bottom of the page and click **Get Started**.

![twitter-api-get-started](https://user-images.githubusercontent.com/31993566/215387606-c06a81f8-13eb-420b-a543-9bcf52ff5086.png)

Click **Apply for a developer account**. 

![developer-account](https://user-images.githubusercontent.com/31993566/215394529-308ccd06-13c2-4d0a-ab30-10678d10131c.png)

Note that you will need to have a verified telephone number associated to your account. If you haven't done it yet, you will see the relevant message - click the button **Add a valid phone number** and follow the instructions.  Click **Next**.

![essential-access-questions](https://user-images.githubusercontent.com/31993566/215394628-5331eda3-0d08-4538-b787-09fca73144af.png)

Fill in the data in the needed fields.  Click **Next**.

![fill-in-the-required-fields](https://user-images.githubusercontent.com/31993566/215394694-1192c002-e361-4ec0-90e1-ae5d5b3555ee.png)

Accept the Developer agreement & policy.

![developer-agreement-policy](https://user-images.githubusercontent.com/31993566/215394773-88bfaeeb-3fe6-4400-bcec-f896274fef42.png)

Verify email.

![verify-email](https://user-images.githubusercontent.com/31993566/215394820-5947b0f1-4816-4728-a33c-0a53d10b94b8.png)

After email verification, create a App. Give it a name and click **Get keys**.

![create-app-get-keys](https://user-images.githubusercontent.com/31993566/215394864-b9a4310a-1752-41d3-8026-235ac8a706b0.png)

# Upgrade to Elevated access
Here are the steps to apply for elevated access on the Twitter developer portal:

Go back to the Developer Portal. Navigate to **Products → Twitter API v2 → Elevated**, then click **Apply for Elevated**. 

![apply-elevated-access](https://user-images.githubusercontent.com/31993566/215394912-6416e8ab-2eba-4e59-ba28-2d2860ac57a6.png)

On the next step, fill the fields with basic info and click **Next**.

![basic-info](https://user-images.githubusercontent.com/31993566/215394962-3c9c54ac-a51b-492d-a3a7-08395cc33bc6.png)

On the next page, you need to give detailed answers to the set of questions about how you are going to use Twitter API. When you finish, click the button **Next**.

![intended-use](https://user-images.githubusercontent.com/31993566/215395058-e6d32aed-20ac-4435-802d-d3b79642c266.png)

On the next page  Review you can check your data and answers. If everything is ok, click **Next**.

![apply-elevated-review](https://user-images.githubusercontent.com/31993566/215395133-93f10957-2e63-422f-8ccb-858d6026a1b2.png)

Accept the Developer agreement & policy. Click **Submit**.

![developer-agreement-policy](https://user-images.githubusercontent.com/31993566/215395247-112331ed-f117-4f95-ae0d-8fadc7ba53f2.png)

You will receive an email from Twitter once the Elevated access application has been approved.

![developer-account-approved](https://user-images.githubusercontent.com/31993566/215395341-beb60562-1928-4e5e-a87e-9c7a0171a1c6.png)

Go back to Developer Portal and copy the keys and access tokens.

![api-keys-tokens](https://user-images.githubusercontent.com/31993566/215395416-ed3b5e5d-a61d-4676-abdb-14b7dc08c073.png)



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
