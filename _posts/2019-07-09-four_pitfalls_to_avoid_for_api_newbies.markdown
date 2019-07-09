---
layout: post
title:      "Four pitfalls to avoid for API newbies."
date:       2019-07-09 14:54:09 -0400
permalink:  four_pitfalls_to_avoid_for_api_newbies
---





I recently had my first API experience, for the newbies like myself, API is shorthand for Application Programming Interface. You’ve probably heard the term and you’ve mostly definitely been a beneficiary of APIs as they have become a ubiquitous component of most popular apps. 
So what exactly is an API? Well, I’ll let this [video](https://www.youtube.com/watch?v=s7wmiS2mSXY/) be a much better guide than I can be.


 
Seems like a relatively simple concept, but  for new programmers attempting to use an API  in your app for the first time can definitely be an adventure. For a developer with any amount of API experience this will all seem very obvious, but for those new to APIs, here are four lessons I learned about using APIs.  

**1)	Access is limited** 

In hindsight this seems too obvious. Most apps limit the information that can be accessed via their API. So confirm the data you need is accessible via a given API. 

Even if the data is available in the API check to see if there are any costs or prerequisites for gaining access to the API. For example Google has an API for basically everything from Gmail to Gcloud, but there are fees associated with gaining access to certain Google APIs. Also, other app’s like Indeed.com have certain prerequisites before users can gain access to their API, and as such require all potential users of their API to go through application process(needless to say coding students are not likely to get approved.)

**2)	The Data Format**

Check to make sure the data from the API can be retrieved in the desired data format, most APIs will offer multiple data formats ranging from JSON to YAML, but some may only offer JSON or XML. Make sure you’re a
pp is setup to parse the correct data format. 

**3)	Keep Track of your API key**

When you get access  to certain secure API’s (i.e. any google API) you are provided with an API Key. An API key is basically a very long and complex access code that allows your app to connect to certain  APIs. I committed the ultimate newbie mistake. I saved my API Key inside a notes file which accidently loaded up to GitHub with rest of my app, thus making my "secret" API Key available to anyone with access to GitHub.  

**4)	Data Volume**

   When I first ran my CLI app after connecting to the API, it kept pulling data until I forced the program to shut down. So, the lesson derived from this experience is: know how much data to expect and create the appropriate methods to limit the amount of  data points to be pulled per API request, otherwise your program could pull data all day. 

      
Hopefully, that helps set some expectations in regards to using APIs, but know that APIs are an extremely powerful and at times complex tools. So, learn as much as you can about API, because odds are you will be using them in your coding career. 

Enjoy coding.   



