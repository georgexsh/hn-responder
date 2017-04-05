# hn-responder
Python script that replies to every @newsycombinator tweet with a link to the comments page.

This script uses the Twitter Streaming API and Hackernews API via Firebase. It reads all tweets for the authenticated Twitter account and puts them into a queue. A background thread takes the tweets from the queue. If a tweets is from the @newsycombinator account, the background thread goes through all top Hackernews postings via the Firebase API and select that posting that matches the title of the tweet. It then sends out a reply tweets with the link to the comments page of the Hackernews posting.

## Setup

To run the script, use the following steps:

1. Install the Python modules `requests-oauthlib` and `python-firebase`:
        ```
        pip install requests-oauthlib
        pip install python-firebase
        ```

2. Create a Twitter app on https://apps.twitter.com/app/.  Get the tokens and secrets for your Twitter app on the "Keys and Access Tokens" page.

3. Create file `twitter-secrets.json` with following contents (replace with your actual tokens and secrets):
        ```
        {
            "access_token": "12345",
            "access_token_secret": "abcdefg",
            "consumer_key": "1q2w3e4",
            "consumer_secret": "ABCDEFG"
        }
        ```

4. Execute script `hn-responder.py` from the command line. Note that it will run forever until killed.
        ```
        python hn-responder.py
        ```
