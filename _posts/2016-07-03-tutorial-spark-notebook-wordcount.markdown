---
layout: post
title:  "Intro. to Apache Spark and Python Notebooks"
date:   2016-07-03 09:00:00 -0500
categories: [tutorial, apache, spark]
caption: This video walks you through a Python Notebook that uses Apache Spark to analyze the Back to the Future transcript.
super: unofficial
tags:
- spark
- notebook
- jupyter
- python
---

![Super Unofficial](/img/profile0.jpg){: .post-content-profile } In this video I'll show you how to use Python Notebooks and Apache Spark
to perform simple analysis on the Back to the Future transcript.

The source code and Docker Compose config for this tutorial can be found at:

[https://github.com/markwatsonatx/tutorial-spark-notebook-wordcount](https://github.com/markwatsonatx/tutorial-spark-notebook-wordcount)

Clone the repository, run "docker-compose up -d" and you'll be up and running!

This tutorial uses a Docker Image that I created and can be found at:

[https://hub.docker.com/r/markwatsonatx/spark-notebook](https://hub.docker.com/r/markwatsonatx/spark-notebook)

The Docker Image contains Apache Spark 2.0.0-preview pre-built for Hadoop 2.7. It also includes Python 3.5
and [Anaconda](https://www.continuum.io/why-anaconda) for running [Python Notebooks](http://jupyter.org/).

The Dockerfile can be found at:

[https://github.com/markwatsonatx/Dockerfiles/tree/master/spark-notebook-2.0.0-preview](https://github.com/markwatsonatx/Dockerfiles/tree/master/spark-notebook-2.0.0-preview)

<iframe width="640" height="400" src="https://www.youtube.com/embed/zy9JB7sxjGs" frameborder="0" allowfullscreen></iframe>