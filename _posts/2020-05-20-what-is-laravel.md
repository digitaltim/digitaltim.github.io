---
layout: post
title: "What is Laravel?"
date: 2020-05-20
---

Now that I have a working installation of Laravel running on Homestead it's time to review what Laravel is... At this stage of my career with web application development, there are many concepts and features that I have never used. However, it's a good idea of start the process of getting familiar with Laravel by reading the 'Getting Started' documentation. I've already gone through what I needed in the 'Installation'[^1] and 'Homestead'[^2] sections. I'm specifically choosing to stay on the 6.x LTS branch for this project, even though there's a newer 7.x release. Thus my references will be limited to the 6.x documentation.

Laravel is a very feature rich framework. There's a lot in here that I probably won't use on this project and may never use. Yet I prefer to review what's available in the documentation so I at least attempt to become familiar with what's possible and offered. I also find that I learn a ton just by doing this. Starting with the 'Configuration'[^3] section I learn how to use the environment configuration. I especially like the 'Maintenance Mode'[^4] feature which is something I cannot as easily do in most applications I've worked with in the past. It's also nice to test drive some of this functionality as I read through each section creating some muscle memory mappings back to the concepts.

Next up is the 'Directory Structure'[^5]. There's a lot going on here and this highlights how flexible the Laravel framework is. There are lots of ways to setup the structure and it's been mostly standardized through a set of Artisan commands to generate the base classes. This much information can be overwhelming, but it's nice to see what's under the hood. Specifically why certain directories are in the default project structure. And conversely what's not in the default structure but could easily be added through an Artisan command. 'The Policies Directory'[^6] stood out for me because a large part of the reason I'm even using Laravel is to reuse authentication/authorization functionality from another application that's using Laravel. I quickly looked at the other application's directory structure to see if authorization was setup using this approach. It's not but it's a great place to start a list of questions that I'll need to answer. It's also a great way to compare implementations and possibly switch to this or another approach down the road.

Finally we have 'Deployment'[^7] section. Optimization for deployment is the bulk of what's covered. I wonder what a non optimized application's performance hit would be? It would be nice if they listed some metrics or examples. The great thing about Laravel is that it's open source. So if I wanted to contribute to the documentation, in theory, I could. Lastly, Laravel Forge[^8] appears to be an interesting resource. I'll have to add that to my list of things to explore further.

I've officially hit my limit with reading the Laravel documentation... There are more important areas to cover, like 'Architecture Concepts', but I want to move on for now... If I were going to run a conventional Laravel applicaiton using Blade Templates and server side rendering, I'd probably want to go a little deeper. But I know that I'm mainly going to be setting up a RESTful API and likely use Vue.js as my frontend. Thus I've gotten a lay of the land and need to move on to getting started with Vue.js[^9]...

[^1]: [Laravel Installation](https://laravel.com/docs/6.x/installation)
[^2]: [Laravel Homestead](https://laravel.com/docs/6.x/homestead)
[^3]: [Laravel Configuration](https://laravel.com/docs/6.x/configuration)
[^4]: [Laravel Maintenance Mode](https://laravel.com/docs/6.x/configuration#maintenance-mode)
[^5]: [Laravel Directory Structure](https://laravel.com/docs/6.x/structure)
[^6]: [Laravel Policies Directory](https://laravel.com/docs/6.x/structure#the-policies-directory)
[^7]: [Laravel Deployment](https://laravel.com/docs/6.x/deployment)
[^8]: [Laravel Forge](https://laravel.com/docs/6.x/deployment#deploying-with-forge)
[^9]: [Laravel JavaScript & CSS Scaffolding](https://laravel.com/docs/6.x/frontend)

