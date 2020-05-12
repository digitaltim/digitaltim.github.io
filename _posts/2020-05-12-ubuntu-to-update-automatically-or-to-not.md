---
layout: post
title: "Ubuntu: To Update Automatically or To Not..."
date: 2020-05-12
---

Coming from the world of Windows and Ubuntu Desktop versions, updates are kind of important. They provide bug fixes and enhancements. In the past I've configured my systems to notify me when updates are available but not automatically download or update. I felt in control by reviewing the changes before applying them to my system. Yet as time went on, I found myself less and less looking at the changes and just blindly applying them to complete the task. This is especially true in the mobile space where apps are being updated on a seemingly continuous basis. In the production server world, the approach appears different. Change is risky and needs to be understood before accepting.

As a developer, I've always had to do a bit of the **DevOps** on my own. Now, working for a larger company with a smallish IT department, I've had to maintain PCI compliance as part of my domain of responsibilities. This has generally meant venturing into the world of **system administration**. There's a bit of cross domain knowledge both developers and system administors have... In the case of PCI compliance, at least in terms of the issues that have come up, I've been the one to take on the tasks.

All of that leads up to a discovery I made during our last round of PCI compliance testing. When I attempted to update the system software, mainly Apache, I found the system in a defunct state where the `/boot` partition was full. The first time I hit this snag, I tried to just fix it instead of searching for the underlying cause. However, when I had another round of the same issue, needing to update Apache, and noticed the /boot drive was full again, I decided to investigate why this is happening. After all, I didn't update the system.

The interesting part about this is that I had no idea our system administrators policy is to not auto update anything. So it's a bit of a paradigm shift for me. Yet at the end of the day my task is now a bit more complicated. I have to fix the underlying issue before I can move on to correcting PCI compliance. Though complexity creep is a bit of a norm in the world of software, per my experience. It's generally never as straight forward as it first appears. Yet the optimist in me tends to forget this experiential historical record.

So what's auto update anyway? It's actually a bit complex in the Ubuntu server world because there are many options to configure. Luckily I think it has to do with a package called `unattended-upgrades`. [^1] Issuing the command `dpkg -l unattended-upgrades` shows this package is installed. [^2] So now the complexity ensues and I need to figure out how to remove this properly and check to see if the system no longer updates automatically. Anytime I start to tweak things, I like to try to understand exactly what I'm doing. Yet on some level, I can only know with confidence as far as my knowledge goes. So there must be a balance. And of course there are always multiple ways to accomplish something and depending on what someone else learned, answers found will be biased towards their knowledge depth. Furthermore complicating matters is the versions of software that I'm working with versus what system is being refereced... Managing this complexity and coming up with a plan takes effort.

I first want to confirm that I'm using the right command. Since I don't do this very often I'm also confronted with the challenge of an additional re/learning curve. I search for "how to use dpkg to view if a package is installed". First hit is Stack Overflow.[^3] This now starts to get a bit hairy as there's a lot of information that I have to parse through. Back to the search results and the second hit is simpler.[^4] I even figure out there's likely a better command to use: `dpkg -s unattended-updates`. Sometimes finding a website that offers a tutorial is better than Stack Overflow where user's post solutions and then upvote for consensus. The result is clear:

    dpkg -s unattended-upgrades
    Package: unattended-upgrades
    Status: install ok installed
    Priority: optional
    Section: admin

Now, the question becomes, how do I uninstall it? First, I want to know what's actually installed. I have to go back to the Stack Overflow result and use another command to list everything the package contains. I found a good article listed there.[^5] What's interesting is there's a log in `/var/log/dpkg.log` that should contain all the history if I wanted to track down who installed this pacakage... Though that's a whole other direction to take things. Yet looking in the last log I can see that dpkg last tried to run `2020-03-18 06:41:06`... That seems like when the /boot partition got full! Anyway, I think I'm ready to test what would happen if I removed the package with: `dpkg --dry-run -P unattended-upgrades`

Decided to go back a little and look at those logs a little more... Needed to figure out how to. Found a decent tutorial and used `zcat /var/log/dpkg.log.2.gz`.[^6] Not sure I can tell what's going on. I think the resolution is to just uninstall the package.

[^1]: [AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates "This is a simple tutorial that will teach you to configure your system to automatically install security updates.")
[^2]: [dpkg](https://wiki.debian.org/dpkg "a medium-level package manager for Debian")
[^3]: [How do I check if a package is installed on my server?](https://askubuntu.com/questions/423355/how-do-i-check-if-a-package-is-installed-on-my-server)
[^4]: [How to find out if package is installed in Linux](https://www.cyberciti.biz/faq/find-out-if-package-is-installed-in-linux/)
[^5]: [15 dpkg commands to Manage Debian based Linux Servers](https://www.linuxsysadmins.com/15-dpkg-commands-in-linux-servers/)
[^6]: [How To Read And Work On Gzip Compressed Log Files In Linux](https://itsfoss.com/read-compressed-log-files-linux/)
