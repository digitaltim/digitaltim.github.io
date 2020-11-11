---
layout: post
title: "Learning Tailwind CSS - Part 3"
date: 2020-11-11
---

Back to [Tailwind CSS](https://tailwindcss.com/ "Tailwind CSS is a utility first CSS framework.").

Maybe I should be calling this Day and not Part since I end up consuming a day to complete a part... Semantics... I'm pretty excited today about diving in a little deeper. Although much of what I reviewed yesterday wasn't immediately useful, it does plant seeds for future steps. I definitely can see once I get past the basics, I'll want to package up and customize the tools for more advanced designs. It's kind of neat to survey the project a little and see the scope of possibilities and how well thought out the tooling is. It also is kind of important to get a bigger perspective because it points to the practical realities of mananging sufficiently complex projects.

Let's being the process of Layout with Container[^1]. It's an interesting approach to making a nice responsive layout. Even if it doesn't reflow content to take advantage of extra screen real estate, it makes the content fit the viewport. The customization section is helpful for reducing repetition for common settings.

Next up is Box Sizing[^2]. I think about the box model of CSS. This seems useful if I need to specify exact sizes of containers. Could even use these to have responsive variants... I'll make a little demo to play with this concept. For some reason I prefer to include borders and padding. Yet even with this, I'm wanting to jump ahead to the flex box model of layout... Need to take it one step at a time.

Moving onto Display[^3]. Block, Flow-Root, Inline Block, Inline, Flex, Inline Flex, Grid, Inline Grid, Contents, Table, Hidden, Responsive variants... These are a little tricky actually. I ended up creating a demo that defaults to block but at the medium break point changes to flex. This seems like the typical setup where mobile you want to stack items and as you widen the screen the reflow to use more of the realestate. I also had to get some practice undoing things like margin that make sense when block but don't when displaying flex, etc. Good little bit of practice.

Next up is Float[^4]. Very nice feature for sure. If you have a container with multiple elements, this allows the spatial relationship to be adapted as needed. I like the idea of hover being activated for the pseudo-class variants... Could be fun to move items around when you hover over them as a game almost.

Going to wrap up with Clear, Object Fit, Object Position, Overflow (this ended up fixing my test table that overflowed it's parent container!), Overscroll Behavior, Position (These are interesting and will require some deeper experimentation to understand), Top/Right/Bottom/Left (these also seem really useful when using absolute positioned elements), Visibility (this also seems to be useful for hiding things but keeping them in the DOM), Z-Index.

My overall takeaway from today is that there are likely a lot of ways to control the layout of a page. I'm likely going to need to spend some time experimenting and trying different approaches. I'd imagine there will likely be a deeper understanding gained when I have more practice. All cool stuff though.

[^1]: [Tailwind - Layout - Container](https://tailwindcss.com/docs/container "A component for fixing an element's width to the current breakpoint.")
[^2]: [Tailwind - Layout - Box Sizing](https://tailwindcss.com/docs/box-sizing "Utilities for controlling how the browser should calculate an element's total size.")
[^3]: [Tailwind - Layout - Display](https://tailwindcss.com/docs/display "Utilities for controlling the display box type of an element.")
[^4]: [Tailwind - Layout - Floats](https://tailwindcss.com/docs/float "Utilities for controlling the wrapping of content around an element.")
