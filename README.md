Data mining using the Twitter Streaming API
===========================================

This project utilizes the [Twitter Streaming API](https://dev.twitter.com/streaming/overview)
and [Tweepy](http://www.tweepy.org/) to collect potentially large amounts of
tweets from the public stream and store them in a database.

Important Notes
---------------

* **Performance:** This is a work in progress. There are various performance and
  parsing improvements to be made!

* **Sentiment Analysis:** This is a *VERY* naive implementation of sentiment
  analysis. Sentiment analysis is a very complex subject, and I have no
  intention of covering all the intricacies involved.

  Instead, this project employs more of a "shotgun" approach - While this
  implementation of sentiment analysis may not be very accurate for a small
  amount of information, the hope is that with very large sets of information we
  will get a generally accurate result.

  We also currently only support English language input. **Be warned,** this
  results in a lot of neutral results (for example, a Spanish language tweet
  will be classified as neutral, regardless of what it says), so use the neutral
  result at your own risk.

* **Databases:** There is currently no functionality to update database schemas
  if/when they change. This means old databases *may* not work as expected.
  Pulling some things like text out of a database generated by this project
  should work regardless of the database's age.

Usage
-----

1. Create an application on Twitter and obtain your consumer/access tokens. (for
more information on creating a new application, see [here](https://dev.twitter.com/)).

2. Once you have obtained your tokens, place them in a CSV file,
"credentials.csv" with the following format:

   ```
   consumer_key,YOUR_CONSUMER_KEY_HERE
   consumer_secret,YOUR_CONSUMER_SECRET_HERE
   access_token,YOUR_ACCESS_TOKEN_HERE
   access_secret,YOUR_ACCESS_SECRET_HERE
   ```

   If you are using [Plotly][https://plot.ly/] for any data graphing, include
   the following lined in the "credentials.csv" file:

   ```
   plotly_username,YOUR_PLOTLY_USERNAME_HERE
   plotly_api_key,YOUR_PLOTLY_API_KEY_HERE
   ```

   *Warning: Keep your keys/tokens a secret!*

3. From the command line, run collect.py with the terms you wish to collect
   tweets about:
    ```
    python collect.py "YOUR SEARCH TERMS HERE"
    ```

4. Collect tweets for however long you wish. Tweets collected since running and
   database file size (in KB) will be shown at the command line.

5. Run one of the parsing scripts to parse/graph the data.


TODO
----

1. (Optional) Take collection time as argument
2. Script/function for clearing database.
3. Clean up directory structure.
