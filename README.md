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
    "5zl5i3": {
        "url": "https://www.reddit.com/r/aws/comments/5zl5i3/aws_dynamo_limitations/",
        "title": "AWS Dynamo limitations",
        "comments": [
            "Do you even have a rough estimate of write rate? That's usually a solid place to start, e.g. \"User login\", \"User search for\", \"User make action Y, W, Z\".. that's 5 values or 2.32 bits. User and target object IDs are 64 bits, so that's 16.29 bytes/record. User-specified query string up to 60 bytes in 20% of events, that's 28.29 bytes/record, 100 requests/sec? That's 2.76kb/sec, etc. ",
            "Have you talked to AWS directly?  They have a lot of folks that can help you figure out the best AWS specific (or 3rd party in some cases) solutions. You have an account rep regardless of support tier.  I would reach out and start a conversation, they may at least be able to give you some guardrails to operate with. ",
            "with a lot of traffic, would be impossible to catch all this info in our relational database. This sounds like a use case for kinesis firehose. You probably want to look into the full suite of analytics offerings that AWS has. I'm only passingly familiar with any of these tools.  But there is a full suite of analytics tools and services that maybe more to your use-case than just a DB, be it relational or not.  Especially given the desire to not deal with infrastructure. Depending on your search needs elasticsearch or Athena could serve your needs.  There are really so many ways to deal with data in AWS that it almost takes talking to a service rep to get a handle on what is truly possible. ",
            "Kinesis Firehose to Redshift may be a better fit but Redshift has its own set of limitations that may not work for you. I'm a big fan and user of DynamoDB but you requirements or maybe your approach to using DynamoDB may not be a good fit.  ",
            "Snowplow  ",
            "kinesis to s3 files. athena to query the files. or bulk/batch load into Redshift. if you want search, elasticsearch to index if sql is not enough and you want to pay, although the events you're logging is just trash events so Redshift or Athena sounds fine. Athena queries files so you aren't paying for a running DB instance. If your want to dump everything into a dumpster and worry about it later then dig through your unstructured mess later and slower, use EMR/Hive. If you want Dynamo, you can store a pointer to an S3 file for documents > 400KB. You also aren't describing your use cases. Why are you choosing DynamoDB? When info are you vending? Also: Proposed products/architectures is like on the front page of Amazon: https://aws.amazon.com/kinesis/firehose/ ",
            "Do not, I repeat, do not use DynamoDB, like for anything or you will suffer from extreme vendor lock and likely a bunch of logic hacks to make it fit your model. I know this because I went through it last year. Also the aws dynamo sdk was responsible for an incredible amount of network lag on our api.  I second the other commenters'  Kinesis Firehose recommendation. Specifically how our analytics platform works is Firehose sends data every minute or when a 5mb buffer is reached to S3 (files aggregated by the minute, Firehose does this automatically). Then an AWS Lambda function processes each file when it's written, splits the file by line, and writes the data to AWS ELASTICSEARCH. I capitalized ELASTICSEARCH for effect. You should definitely use ES. "
        ],
        "Question": "We are developing an activity log/control for our system. For example, user login, user search for X, user make action Y, W or Z and we want to register all this data. For this type of problem our first idea was NoSQL, as we are SaaS product with a lot of companies and users, so will be a lot of data, and we need fast response to save and get all the info. At our first glance, we thought about google firebase, but it was not exactly what we were thinking about, as our engine will need some complex queries and no real time feature. Mongo seems to be ok, but we don't want more server/infra worries with clusters, replications, and so on.. Our infra is entirely located at AWS, so DynamoDB would be great, but after some tests we definitely would be screwed up with all the limitations about 400kb documents, or 1MB to get data, even a maximum of 100 options to be passed on IN statement. There are a lot of systems with these activity log, but as we are a SaaS product, with a lot of traffic, would be impossible to catch all this info in our relational database. What would you suggest for problems like this? "
    }
}
