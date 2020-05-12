---
layout: post
title: "Git Workflow Insights in One Context"
date: 2020-05-12
---

I found myself being somewhat inefficient while working on a project... until I finally hit a threshold of pain and decided to change. At work, we have our infrastructure on premisis, virtualized and following a high level standard/best practice workflow. Yet depending on the context, how I interact with the servers and related code might differ slightly.

We generally have three servers for each resource:
- development
- staging
- production

The names are kind of self explanatory but the respective configurations and use cases vary slightly which are based upon somewhat soft and at times hard guiding principles. Initial code changes and some functional testing occurs on DEV (development). Generally DEV is not meant for end users because the code might contain debug statements/output that can cause confusion to the untrained eye. When an enhancement, bug fix, feature request is complete, from the developers point of view, the code changes are committed using a version control system, in a new branch whenever possible. There are system level rules in place to prevent code from being committed to the main production branch without an approved ticket in our issue tracking system. But depending on the type of change things could be fast tracked and skip some of the nuanced steps one might take if significant functional changes are being made. However, the issue tracking system is in place for traceability requirements our organziation has to adhere to.

Next the changes are brought into STG (staging) for user acceptance testing. Typically STG will be set to run the new code by checking out the branch containing the changes. Once the user tests and accepts the changes the code becomes ready for release to PRD (production). Having changes isolated to a branch allows STG to be set to different versions of code for testing different sets of changes. Often times these servers are shared resources and changing the code that's being currently run is relatively easy by having it isolated to branches.

Finally when the changes are ready for release to PRD, the final steps involved are:
- creating a contigency plan to keep the system operational in case a bug is discovered after deployment
- approval in the issue tracking system from an oversight authority
- merging the development branch into main/head
- committing the merge to main/head referencing the approved issue (administrative control in place)

It's helpful to synthesize those details but the main point of the post is to describe my development process. Since DEV is a live server, I connect to it over SSH and use the terminal to search and make changes. I consider this the "hardcore" programming approach as the command line is very efficient, if you know how to use it well. Yet it's also a bit heavy and doesn't have all the tools a modern workflow uses. I use Microsoft Visual Studion Code as an editor which has wonderful features that enhance productivity without the need to be an expert in command line tools...

Thus I need a way to run the code I work on. It takes time to fully setup tooling so I've chosen to syncronize with DEV from my local environment. Yet a few weeks ago I was asked to take a look at something and explain how it worked. I naturally started to poke around on DEV through the command line. I started making changes and then quickly decided to go deeper on my local copy of the code using Visual Studio Code. I ended up making my changes locally and copying them manually on DEV to keep things in sync. This workflow went on for days as I started getting deeper. Initially I thought this would be a quick task but it developed into a bigger project. Thus my workflow was becomming unsustainable and I had to change my approach.

I wanted to document how we use a distributed version control system in a centralized way. The short of it is that I needed to create a branch, clone a copy locally and syncronize my local changes to DEV for testing... Atlassian has some great documenation explaining the process.[^1] [^2]

[^1]: [git clone](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-clone "Here we'll examine the git clone command in depth.")
[^2]: [git checkout](https://www.atlassian.com/git/tutorials/using-branches/git-checkout "This page is an examination of the git checkout command.")
