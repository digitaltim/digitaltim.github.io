---
layout: post
title: "Learning Tailwind CSS - Part 5"
date: 2020-11-16
---

Back to [Tailwind CSS](https://tailwindcss.com/ "Tailwind CSS is a utility first CSS framework.").

Taking a step back and looking at the bigger picture... Flex vs. Grid[^1]. I think for my purposes, I'm going to use grid. I have a few layouts in mind that I want to be specific about for different breakpoints. I think it makes sense to put these areas onto a grid and choose the placement/arrangement when changing screen size. I do like the idea that flex can make sure a bunch of content flows well as it's all there on the page. Since I have very specific content that's limited, it makes more sense to do grid. If I had a bunch of similar but random amount content I'd explore flex...

Yet even Tailwind sort of provides this hybrid grid/flex solution[^2]. I kind of get each small example, but I don't yet understand when to pull out a particular solution. I think narrowing my focus to grid will help me at least get some practice and hopefully some deeper understanding... Overall I don't feel confident with anything. I have this idea in my mind, but translating that to code is not straight forward. Luckily I'm sort of able to break it down into smaller pieces.

Sometimes it's good to get a taste of other perspectives. This one compares Bootstrap grids to Tailwind grids[^3]...

[^1]: [Quick! What’s the Difference Between Flexbox and Grid?](https://css-tricks.com/quick-whats-the-difference-between-flexbox-and-grid/ "Let’s go rapid fire and try to answer this question with quick points rather than long explanations.")
[^2]: [Flexbox Grids](https://tailwindcss.com/components/flexbox-grids "Examples of building Flexbox grid layouts with Tailwind CSS.")
[^3]: [Recreating Bootstrap Grid with Tailwind CSS Grids](https://dev.to/praveenjuge/recreating-bootstrap-grid-with-tailwind-css-grids-6j0 "Bootstrap grid is powered by flexbox...")

