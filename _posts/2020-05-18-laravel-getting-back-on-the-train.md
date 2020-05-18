---
layout: post
title: "Laravel: Getting Back on the Train"
date: 2020-05-18
---

I started the process of leanring Laravel about nine months ago and then it fell off my radar as other tasks came up. My latest project started with an old PHP code base that I've invested time in to understanding how it works. In determining next steps for the project a lot of features and enhancements have been requested. One larger feature in particular, adding authentication to access the application and authorization for creating different roles giving users access to different features appeared to be the place to start.

I consider this one feature from the business case perspective of having similar functionality to other applications. The idea here being to reuse existing functionality if possible. Thus my next discussion was with the developer who implemented the latest incarnation of that functionality. Which opended the door to something I knew about but kind of forgot about until now. The prior developer before me started rewriting the very application I've been tasked with improving.

After taking a look at how far along they were able to take things and getting a quick tour of how I would add the authentication/authorization piece to my project it became clear I should probably pivot. Instead of trying to work this functionality into the legacy code base I could reuse the produciton code's approach which is based on Laravel and uses some packages that integrate well into the framework. In addtion I could use the new project as a starting point or as a guide to what the future applicaiton should start to look like. 

Just when I thought I was getting some momentum I have to pivot and hop on another learning curve. The new problem is figuring out how to get started. On some level I have to figure out where I left things.

Laravel is great in the sense that's it's very feature rich and well documented. Though it's also a fast moving system. In the nine months that I've had my job they've made two full major version releases. I think when I started they just transitioned to the 6.x version. Now they're on the 7.x version. I need to figure out what tooling I setup, if any of it needs upgraded, how to upgrade it and then test with a 'hello world' type of project. Also, I need to make sure I'm running on the LTS version of Laravel since our organization requires that we maintain high levels of security in our development process. 

It's starting to feel like I have a lot of little decisions that I need to tackle just to get started. Though the barriers might be small on their own as a collection it's making the process a bit frustrating. I also feel like I kind of have to start from scratch to make sure I'm following the best practices and doing things correclty. Taking a step back and looking at this from a higher level perspective, I realize that I have yet to build, deploy and support a Laravel project. Thus it makes sense to slow down and pay attention to details so I can be confident I'm doing due dilligence.

Lastly, I got pretty excited when I first learned that I should probably pivot. Even more excited when my boss agreed and gave me approval. Then my balloon kind of deflated when I realized what getting started meant. Would it be easier if I hadn't installed a bunch of tools already and done some practice projects by being able to start from scratch? I don't know. What I do know is that I need to figure out what needs to be updated and changed to start developing following the latest guidelines. So that's my next step.
