---
layout: page
title: About
permalink: /about/
---

![Me, a long time ago](/img/profile0.jpg){: .about-profile } This is me a long time ago on an RV Trip in Kent, WA.
I travelled around the US for 3 months with my wife, and I forgot to shave :)

![Me, now](/img/profile1.jpg){: .about-profile } This is me now in Ausin, TX. I am a Developer Advocate for IBM, Cloud Data Services.
I'm all grown up and super professional. I have kids and everything.

I'm going to put stuff here that may be useful. Please follow this key:

![Me, now](/img/profile1.jpg){: .about-profile2 } = stuff that comes from [my super official IBM blog](https://developer.ibm.com/clouddataservices/author/markwats/). 

![Me, a long time ago](/img/profile0.jpg){: .about-profile2 } = stuff that comes from my super unofficial brain and posted here.

## Tutorials

I will be posting tutorials here as often as I can. My goal is to tackle small topics in self-contained tutorials
that you can easily download, run, and expirment with. The only requirements to run these tutorials will be:

1. IDE - Any IDE you prefer
2. [Docker](https://www.docker.com/) ([for Mac](https://www.docker.com/products/docker#/mac), [for Windows](https://www.docker.com/products/docker#/windows), [for Linux](https://www.docker.com/products/docker#/linux), [Toolbox](https://www.docker.com/products/docker-toolbox), etc.)

I plan to use Docker Compose for every tutorial. This will allow you to install and experiment with each tutorial
without having to download and install anything on your machine (except container images of course). 
For example, if I create a tutorial on RethinkDB using Node.js you will not have to download and install RethinkDB or Node.js.
You can simply run "docker-compose up" and the containers running RethinkDB and Node.js will automatically be downloaded and started. 
The source code of the tutorial will be automatically mapped to the containers, so you can experiment with the source code and 
immediately see your changes. 

For more information on Docker Compose [go here](https://docs.docker.com/compose/).

Some other conventions I will try to follow:

* I will map most ports from Docker containers to your local machine (or docker machine) to 30000-something.
For example, RethinkDB port 28015 will typically be mapped to 38015, 8080 will be mapped to 38080.
Node.js port 3000 will be typically be mapped to port 33000.
Use the 30000-something ports to access services running in the containers from your local machine.
When accessing services between containers the containers should be configured to use the standard ports.

* For now I plan on using [Visual Studio Code](https://code.visualstudio.com/download). It is not my preferred IDE,
but it's free and available on most platforms. It has a built-in Terminal and you can easily launch directories from the command line
("code ./tutorial-dir") which is helpful when recording video tutorials. You can use any IDE you prefer.

This video gives you an overview of how the tutorials will work:

<iframe width="640" height="400" src="https://www.youtube.com/embed/wHLhPTYDUYE" frameborder="0" allowfullscreen></iframe>

That's it for now. Please contact me using any of the methods below. Thanks!

-Mark


