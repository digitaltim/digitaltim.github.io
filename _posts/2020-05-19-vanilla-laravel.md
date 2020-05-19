---
layout: post
title: "Vanilla Laravel"
date: 2020-05-19
---

Picking up from my last post I was sitting there with my running vagrant box. I want to start a new project. First I need to logout of and stop myvagrant box: `vagrant down`. Next I need to figure out if I ever installed the Laravel installer using Composer. It appears that it's not because the command `composer global about` does show `%USERPROFILE%\AppData\Roaming\Composer` but when I look in there I don't have the `vendor\bin` directory. So I'm assuming I never installed Laravel installer... I must have used the other way to create projects using `composer create-project --prefer-dist laravel/laravel <project name>`.[^1]

I noticed that my project is based on `Installing laravel/laravel (v7.12.0)`. Since this is just a test, I'll need to figure out later how to base a project on a specific release. But for now I'm going to ammend my Homestead setup to see if I'm at least able to get started... Modify the Homestead.yaml file by adding another folder and site. Then update hosts file at C:\Windows\System32\drivers\etc\hosts. Call `vagrant up` and navigate to the new site.

There's a problem. All the sites I have work but the new one I added. I'm being directed to the first site in the list. How do I debug this issue? I went back and read the documentation for adding more sites.[^2] I needed to run the command `vagrant reload --provision`. It now works.

[^1]: [Laravel Installation](https://laravel.com/docs/7.x)
[^2]: [Adding Additional Sites](https://laravel.com/docs/7.x/homestead#adding-additional-sites)
