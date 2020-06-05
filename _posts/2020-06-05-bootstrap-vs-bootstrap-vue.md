---
layout: post
title: "Bootstrap Vs Bootstrap-Vue"
date: 2020-06-05
---

Reading my last post distracts me a little from why I wanted to make this post... There's almost two weeks passed and I've made some decisions and progress. Yet as I come to the close of another week of work, I'm reminded that it's easy to get fatigued and confused. Especially when on multiple learning curves at the same time.

I got stuck on something simple. I have a row with three columns. I want on xs screens for the first two colums to display and the third to wrap. On sm screens and up I want the three columns to be next to each other...

I think the issue here is that Bootstrap is a CSS framework whereas Bootstrap-Vue is a Vue component library with the Bootstrap CSS framework built in. Thus if I were modifying vanilla HTML I'd refer to the Bootstrap docs... But I need to reference the Bootstrap-Vue docs and there's more to it than CSS...

The condensed version is that I got confused and was mixing the two attribute systems. Sometimes looking at the component reference is easier to see what I'm doing wrong than the examples.[^1] I quickly spotted that I was trying to use a property that wasn't there... This helped me realize I was looking at the wrong documentation, even though it's useful to go back to the source to understand the system and how it works.[^2]

[^1]: [Bootstrap-Vue](https://bootstrap-vue.org/docs/components/layout#comp-ref-b-col)
[^2]: [Bootstrap](https://getbootstrap.com/docs/4.5/layout/grid/#column-wrapping)