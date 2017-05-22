# Reddit Crawler

This crawler uses re, json, urllib, requests and BeautifulSoup packages.

This will generate json files based on the subreddit name.

It crawls the data until the next button disappears in reddit page.

Whenever the next button disappears in the reddit page, it executes the next
subreddit from the list_of_subreddits_to_crawl.

In this we are crawling the title,question,url and list of comments from thread.

**Note :** This code is written in python3


# Required packages installation

Install the required packages using **pip install -r requirements.txt**

# Code Execution

**python reddit_crawl.py**

# Sample Output

{
...."5zl5i3": {
........"url": "https://www.reddit.com/r/aws/comments/5zl5i3/aws_dynamo_limitations/",
........"title": "AWS Dynamo limitations",
........"comments": [],
........"Question": "We are developing an activity log/control for our system. For example, user login, user search for X, ............user make action Y, W or Z and we want to register all this data. For this type of problem our first idea was ............NoSQL, as we are SaaS product with a lot of companies and users, so will be a lot of data, and we need fast ............response to save and get all the info. At our first glance, we thought about google firebase, but it was not ............exactly what we were thinking about, as our engine will need some complex queries and no real time feature. Mongo ............seems to be ok, but we don't want more server/infra worries with clusters, replications, and so on.. Our infra is ............entirely located at AWS, so DynamoDB would be great, but after some tests we definitely would be screwed up with ............all the limitations about 400kb documents, or 1MB to get data, even a maximum of 100 options to be passed on IN ............statement. There are a lot of systems with these activity log, but as we are a SaaS product, with a lot of ............traffic, would be impossible to catch all this info in our relational database. What would you suggest for ............problems like this? "
....}
}
