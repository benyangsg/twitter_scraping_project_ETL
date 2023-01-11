# Twitter Scrapping Crawler
Collects different types of data from Twitter, build your own Twitter data crawler, and store the crawled data in the database.

## Project roadmap

### Step 1: 
Create a developer account on Twitter and obtain your API credentials (Consumer Key and Consumer Secret)

### Step 2: 
Install the python library 'tweepy' using pip by running the command 'pip install tweepy' in your command prompt

### Step 3: 
Import the tweepy library and the other necessary libraries such as 'json' and 'pandas' in your python script

### Step 4: 
Use the API credentials obtained in step 1 to authorize your script to access the Twitter API using the tweepy.OAuthHandler() function

### Step 5: 
Set up the API endpoint using the tweepy.API() function and pass the authorized script as an argument

### Step 6: 
Use the tweepy.Cursor() function to set up a search query to search for tweets based on a specific keyword or hashtag

### Step 7: 
Collect the tweets using the .items() function and store them in a list

### Step 8: 
Convert the tweets into a pandas dataframe for further analysis

### Step 9: 
Use the dataframe to extract the information you need such as the tweet text, user, date and time of the tweet, etc.

### Step 10: 
Use tweepy.Cursor() to query the twitter API for the user Joe Biden, extracting user's profile information, social network information, tweets and retweets and mentions of Coronavirus and Vaccination

### Step 11: 
use json.dumps() method to convert the tweets data in JSON format

### Step 12: 
Use Pandas.json_normalize() method to parse the json object and convert it into a dataframe

### Step 13: 
Save the scraped data in CSV file for further analysis

### Step 14: 
Use the data for sentiment analysis or data visualization for understanding the trend of tweets on Coronavirus and Vaccination by Joe Biden.
