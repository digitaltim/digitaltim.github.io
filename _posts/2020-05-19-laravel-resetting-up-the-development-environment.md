---
layout: post
title: "Laravel: (Re)Setting Up the Development Environment"
date: 2020-05-19
---

I need to take stock of the state of my development environment and figure out what, if anything, needs to be updated to start working on a new project. Often times when starting something new, I look for a good tutorial to follow to limit the noise and get the most signal. Yet in doing so I might gloss over details that are important, like understanding how the tooling works and how to maintain it, for the sake of getting closer to the original goal. But there are other times when more understanding is needed to make progress.

The good thing about Laravel is they have generally excellent documentation. The bad thing is that it moves/evolves fast. So documentation I read nine months ago has changed. What exactly has changed I don't fully know, but I can see the latest documentation has a newer version associated with it.[^1] So maybe it's best to start from the beginning... Again.

There's also multiple paths to achieve the same goal. I'm going to have to figure out which choice I made in the past and look at each step to understand state and whether I need to upgrade/modify it.

Right away I recall that I setup Laravel Homestead on my Windows 10 work machine.[^2] Laravel Homestead is using Vagrant as a foundation.[^3] Vagrant is used to create portable virtual software development environments.[^4] Underneath all of that I'm using VirtualBox to run the environment.[^5] This stack is meant to simplify development but contains a vast amount of complexity. Here are the versions of each I currently have installed and how to check for updates:

- VirtualBox (6.0.14)
    - I get prompted to download the update (6.0.20) when I launch.
    - (6.0.22) is the latest available though on the 6.0.xx branch.
    - Also there's a 6.1.xx branch available.
- Vagrant (2.2.6)
    - Running `vagrant version` I see *A new version of Vagrant is available: 2.2.9 (installed version: 2.2.6)!*
    - There are also instructions provided in the output of this command on how to upgrade.
- Larvel Homestead (virtualbox, 8.1.0)
    - Running `vagrant box list` I see *laravel/homestead (virtualbox, 8.1.0)*
    - What's confusing is that I have a version that appears really old, released on Feb 5, 2019.[^6]
    - How did this old version get installed when so many updates have been released in the time between this release and when I likely installed?
    - The latest release is v10.8.0![^7]

Should I upgrade? Do I need to upgrade? Which ones? If I do, should I keep the old vagrant box around? This is kind of tricky because I have in the past had regressions when upgrading. I suppose the good thing in my case is that I don't have a project that I need to support. So in theory, since I'm starting a new project from scratch, I should be able to just install the latest of everything, as if I didn't have anything installed in the first place. Yet I might blow away the prior Homestead settings that I have... What to do???

Doing a web search and looking for the most current results I start to try to understand what's at stake:

- [How to update your Laravel Homestead Box](https://medium.com/plint-sites/how-to-update-your-laravel-homestead-box-45aabe803ca6)
    - I quickly see that this process can be complicated and care must be taken if you have projects you want to keep around.
    - I also see that I don't fully understand yet what I should do, so I move on.

Back to the search results and I see the top hit is from 2016, which seems really old. But the second hit is the official Laravel Documentation. Looking more closely, I notice an updating section:

- [Updating Homestead](https://laravel.com/docs/7.x/homestead#updating-homestead)
    - I missed this the first time as it's all the way at the end of a pretty extensive table of contents...

Reading through this gave me another idea... to check the branch of Homestead I'm using with `git branch -v`:

```
$ git branch -v
  master  67bbd72 Update golang version to 1.13.1 (#1282)
* release a3534ac Tagging v9.1.0 & Require base box >= 8.1.0
```

Now I see that I'm not actually running 8.1.0 Homestead code but v9.1.0.[^8] This makes more sense since it was released right around the time I set this all up August 31, 2019! However, even as this starts to make more sense I still don't know what the best path is. I'm sensing that I'll be revisiting this subject again a later date when I do actually have a project going and need to maintain the tooling. The goal today is to figure out if I need to update... Since I'm starting to get impatient, I'm leaning towards getting everything updated to the most current version. I also noticed on the VirtualBox Downloads page:[^9]

```
Please also use version 6.0 if you need to run VMs with software virtualization, as this has been discontinued in 6.1. Version 6.0 will remain supported until July 2020.
```

I noticed back on the Laravel Homestead documentation that I can use a VirtualBox 6.x version, so I'm thinking that I don't really think I need software virtualization, so maybe now's the time to hop on the 6.1.x branch... I'm not entirely convinced and am going to check out the search results one last time...

I can see why the post from 2016 is still the top hit: [Keeping your Homestead box Up-to-Date](http://www.darwinbiler.com/keeping-your-homestead-box-up-to-date/). It's short, concise and leaves the impression that the task of updating my tools is important. The one caveat is that I want to make sure this documentation matches the instructions found elsewhere. I also want to replicate the steps he takes. First step is to launch my vagrant box and check what it outputs with `vagrant up`:

```
$ vagrant up
Bringing machine 'homestead' up with 'virtualbox' provider...
==> homestead: Checking if box 'laravel/homestead' version '8.1.0' is up to date...
==> homestead: A newer version of the box 'laravel/homestead' for provider 'virtualbox' is
==> homestead: available! You currently have version '8.1.0'. The latest is version
==> homestead: '9.5.1'. Run `vagrant box update` to update.
```

I also see that I have five projects setup to run on this box. So I want to check them out and just confirm they don't have databases. I'm also curious to find out what I was working on. I opened up the *Homestead.yaml* file and see that the IP address for the system is 192.168.10.10. Hitting this drops me into the first project. There's a sites section that has domain names for each respective site I've created. I see two of them likely have databases but none of it is worth backing up... I was able to figure out that `vagrant ssh` is how you get into the box... 

However, and I'm surprised by this, I'm not going to update anything. I have a working system. I'm going to pivot and move on to getting a new base project up and running. I think part of the reason why is that I'd like to have a Homestead instance per project... I don't think I want to go down that rabbit hole right now... I'll have to circle back at a later date.[^10]


[^1]: [Laravel Installation](https://laravel.com/docs/7.x)
[^2]: [Laravel Homestead](https://laravel.com/docs/7.x/homestead)
[^3]: [Vagrant Development Environments Made Easy](https://www.vagrantup.com/)
[^4]: [Vagrant From Wikipedia](https://en.wikipedia.org/wiki/Vagrant_(software))
[^5]: [VirtualBox](https://www.virtualbox.org/)
[^6]: [laravel / homestead v8.1.0](https://github.com/laravel/homestead/releases/tag/v8.1.0)
[^7]: [laravel / homestead v10.8.0](https://github.com/laravel/homestead/releases/tag/v10.8.0)
[^8]: [laravel / homestead v9.1.0](https://github.com/laravel/homestead/releases/tag/v9.1.0)
[^9]: [Download VirtualBox](https://www.virtualbox.org/wiki/Downloads)
[^10]: [Homestead Per Project Installation](https://laravel.com/docs/7.x/homestead#per-project-installation)
