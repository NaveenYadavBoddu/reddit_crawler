# Reddit Crawler

This crawler uses re, json, urllib, requests and BeautifulSoup packages.

This will generate json files based on the subreddit name.

It crawls the data until the next button disappears in reddit page.

Whenever the next button disappears in the reddit page, it executes the next
subreddit from the list_of_subreddits_to_crawl.

In this we are crawling the title,question,url and list of comments from thread.

**Note: ** This code is written in python3


# Required packages installation

Install the required packages using **pip install -r requirements.txt**

# Code Execution

python reddit_crawl.py
