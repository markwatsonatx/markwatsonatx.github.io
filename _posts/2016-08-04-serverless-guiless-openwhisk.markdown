---
layout: post
title:  "Jess: A Serverless and GUI-less App"
date:   2016-08-04 09:00:00 -0500
categories: [tutorial, openwhisk, serverless]
caption: A Jess is a person who is generous, talented and kindly. The name itself means "wealthy", and this is true, as a jess will always be rich in spirit and personality. Also used by some kids to mean "awesome". -Urban Dictionary
super: unofficial
---

![Super Unofficial](/img/profile0.jpg){: .post-content-profile } It all started with a simple idea -
I wanted to build a super simple app to keep track of my weekly budget. At the beginning of the week I would
set a budget, and every time I made a purchase I would subtract it from that budget.
But I couldn't just build any old app...I had to try something new...

I'm a technology junkie right now. There is seriously something wrong with me. If it's related to software development
or containers I can't get enough of it. I think I watched 20 videos from Dockercon 2016 last weekend. I'm listening to podcasts
every day during lunch on Kubernetes, Mesos, Spark Streaming, and Serverless architectures. In the last 4 months I've built
[iOS apps in Swift](https://github.com/ibm-cds-labs/location-tracker-client-swift), a web app in Angular 2,
a simple head-to-head realtime game in Ionic 2 using [RethinkDB](http://markwatsonatx.github.io/tutorial/rethinkdb/2016/06/24/tutorial-rethinkdb-changes.html),
[a simple Spark notebook that analyzes the Back to the Future transcript :)](http://markwatsonatx.github.io/tutorial/apache/spark/2016/07/03/tutorial-spark-notebook-wordcount.html)
in [Python](https://github.com/markwatsonatx/tutorial-spark-notebook-wordcount)
and [Scala](https://github.com/markwatsonatx/tutorial-spark-notebook-wordcount-scala), and
created this blog with a focus on providing [interactive tutorials using Docker Compose](http://markwatsonatx.github.io/about/).

You get the picture. I love my job, and when I'm not officially doing my job I'm pretty much still doing my job.
I get to learn about tons of new stuff, contribute to open source software, and share what I've learned (still getting the hang of that part).

OK, back to the app...

I didn't really want to spend a lot time building another app. I've been there before - late nights - every night.
So, I got to thinking...you know, like Winnie the Pooh style - think, think, think...

And I came up with Jess:

![Jess Screenshot](/img/serverless0.png)

You can send one of 4 commands to Jess: Set, Get, Add, or Subtract. As long as your message
includes one (and only one) dollar amount Jess will handle the rest. So, with your smartphone or
smartwatch you can simply say "Tell Jess subtract $23 for pizza" (I actually ordered pizza tonight and it did cost $23).  

Jess is just a Twilio phone number. The app is obviously not GUI-less, but I didn't have to design a GUI
(which I suck at) - just like serverless apps aren't actually serverless...which gets us to the backend -
which is, well, serverless :)

The backend is built on [IBM API Connect](https://developer.ibm.com/apiconnect/) and [OpenWhisk](https://developer.ibm.com/openwhisk/).
I'm not running a dedicated web server or container anywhere. The app only runs when a text message is received. 
Here is how it works:

1. User sends a text message to Twilio.
2. Twilio makes an HTTP call to IBM API Connect with the user's phone number and contents of the text.
3. API Connect transforms the HTTP request parameters into a JSON document that [my custom OpenWhisk action](https://github.com/markwatsonatx/jess/blob/master/openwhisk/action.js) can process.
4. API Connect sends the JSON document to my OpenWhisk action's REST endpoint.
5. My OpenWhisk action processes the request - storing user budgets and messages in [IBM Cloudant](https://cloudant.com/).
6. OpenWhisk returns a messaage which includes the user's current balance to API Connect.
7. API Connect transforms the JSON response into a [TwiML](https://www.twilio.com/docs/api/twiml) message. 
8. API Connect returns the TwiML message to Twilio.
9. Twilio sends the message to the user.

In other words:

User -> Twilio -> API Connect -> OpenWhisk -> API Connect -> Twilo -> User

Here is a screenshot of the Assemble tab in API Connect:

![Jess Screenshot](/img/serverless1.png)

So, why go serverless?

1. Because I can.
2. Because I wanted to.
3. Seriously, there are actual benefits like...
4. I don't have to worry about scaling anything (because this app is going to be huge, you know).
5. I only have to pay for API calls (50K free per month) and the time my OpenWhisk actions are executing.

Now, obviously I didn't just create the next Pokemon Go, but I think I built a pretty neat app 
in one night (a very late night) that doesn't require a download or even a mobile web browser
You can run this thing on a flip phone if you want. Along the way I got to learn some cool new things,
and feed this crazy brain of mine.

You can find the source code for the OpenWhisk action (all 125 lines of it!) and the API Connect YAML file
at [https://github.com/markwatsonatx/jess/](https://github.com/markwatsonatx/jess/).