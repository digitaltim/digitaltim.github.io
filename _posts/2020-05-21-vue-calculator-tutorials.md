---
layout: post
title: "Vue Calculator Tutorials"
date: 2020-05-21
---

It's time to start to build out a basic UI for the project. I'm building a calculator of sorts. It's not quite the same as a traditional math calculator but it is similar. The first thing I need to do is create a new git branch using the command `git checkout -b <branch name>`. This creates a new branch and checks it out. For a deeper dive on git branching, Atlassian currates high quality tutorials[^1].

Next I want to quickly get up to speed with how I might approach this. Free Code Camp has a nice calculator tutorial to get started with[^2]. I watched this fully at 2x. Next Traversy Media has a todo list tutorial to get started with[^3]. Got about twenty minutes into this at 2x and decided to pause because both of these are a little different than my workflow. The former doesn't use form elements like I'll likely need to use. The latter uses the vue-cli tool to get started. Maybe I need to look for a Laravel Vue tutorial...

I started to search for 'laravel vuejs tutorial' and found another Traversy Media video[^4]. Yet this felt like a little further down the road from where I am right now. I then decided to look at more search results but nothing stood out. This prompted me to go to the official documentation. I see some video courses linked there[^5]. I realize that I do want to eventually go through an official tutorial series to learn the high level concpets but I also think I'm not fully undestanding what step I'm on. I notice the last free lesson is on forms in the prior video series. So I go back to the official docs and start looking around. I see the last section of the 'Essentials' is on forms[^6]. After taking a quick look at this I realize that my first step should be to work on a quick UI to layout a simple cacluator with static data.

The lesson here is that although the current project that I'm porting makes calls to a DB for getting data associated with the form input, I should limit the scope of this stage to simplify and get familiar with Vue. Understanding how to break down the larger task into more manageable pieces is challenging at times. Especially when I find great tutorials that don't quite do what I need but are enticing enough to want to fully invest my time in. Being able to survey or skim content to get a better idea of the initial approach is a skill I'm still learning. I often find that I'm tempted to follow a video tutorial to "feel" like I've accomplished something. Yet this can be a trap of sorts. Mainly because I end up learning one approach to solving a particular problem that might not match my own set of requirements. Thus trying to piece it all together and understand what I'm trying to accomplish in smaller steps is key. 

One last thing to remember... Run the command `npm run watch` while making changes to vue components so they propogate to the running environment...

[^1]: [Atlassian Tutorial: Git Branch](https://www.atlassian.com/git/tutorials/using-branches)
[^2]: [Build a Calculator with Vue.js](https://www.youtube.com/watch?v=m1_ih43p24s)
[^3]: [Vue JS Crash Course](https://www.youtube.com/watch?v=Wy9q22isx3U)
[^4]: [Full Stack Vue.js & Laravel](https://www.youtube.com/watch?v=DJ6PD_jBtU0)
[^5]: [Intro to Vue.js](https://www.vuemastery.com/courses/intro-to-vue-js/vue-instance/)
[^6]: [Form Input Bindings](https://vuejs.org/v2/guide/forms.html)

