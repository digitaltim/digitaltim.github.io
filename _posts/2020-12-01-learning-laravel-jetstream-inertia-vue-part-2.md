---
layout: post
title: "Learning Laravel Jetstream - Intertia - Vue - Part 2"
date: 2020-12-01
---

I decided to dive into a new project based on [Laravel Jetstream](https://jetstream.laravel.com/1.x/introduction.html "Laravel Jetstream is a beautifully designed application scaffolding for Laravel."). Going down that route I also ended up choosing the Interia/Vue path. Basically, I get Vue.js on the front end, Laravel on the back, Intertia.js as the routing glue to use Laravel's routes. All of this is styled with Tailwind CSS. So I'm trying to learn all of these at the same time. I've dabbled in the past with Laravel and built a front end using Vue via the component library Bootstrap Vue. Slight learning curve...

In my last post I sort of got a lay of the land with how the project is scaffolded, for the most part. Yet today I need to circle back and understand a bit more. This sentence summarizes exactly what I need for my mental model:

>  Inertia is a small library that allows you to render single-file Vue components from your Laravel backend by providing the name of the component and the data that should be hydrated into that component's "props".[^1]

That's it. I want to render single-file Vue components from the backend. Yet I realize that I was going to swap out components from another navbar and have them hydrated from some endpoint. I don't want to reload the whole page. Just the component portion of it... I could just create a whole new page for each component but I think that's the wrong direction. Maybe I'll have to create some API endpoints instead of web routes and use Axios to fetch the data for hydration... Or will I still need some client side routing???

Funny thought the example they reference for routing is 'Profile/Show'. I can't find this route and think it's burried somewhere in the Fortify service provider (actually it's the Jetstream service provider)... Good thing they explain this route is located within the Jetstream application...[^2]. 

> Some of Jetstream's Inertia pages, such as Teams/Show and Profile/Show are rendered from within Jetstream itself. 

I've read through this documentation before but now it's starting to click a bit more.

I'm getting a little off topic but I see now in 'app\Providers\JetstreamServiceProvider.php' where I can set the permissions/roles... Cool. I want to create a user that only can read and not create/update... Created 'Standard' user... Automatically works... Sweet!

I really like the idea of having a form object that standardizes how to work with validation and errors...[^3]. I'm starting to get excited to make something work for my needs. Gotta push forward and not get too bogged down in the nitty gritty...

Now that I've read back through this page, I'm kind of thinking I should build out a new page that uses the Jetstream components, roles/permissions, helpers, etc. stock as they come and not tackle the Tailwind stuff just yet. I can get some practice with this scaffolding and built in features before I try to make it pretty. I kind of already started this process but have a better understanding I think. So I might be able to build something that leverages all of the built in features, then circle back to the Tailwind side and style it how I really want it...

That's the decision I've made and it's coming along nicely!

[^1]: [Laravel Jetstream Interia Introduction](https://jetstream.laravel.com/1.x/stacks/inertia.html#introduction "Laravel Jetstream Interia Introduction.")
[^2]: [Laravel Jetstream Interia Custom Rendering](https://jetstream.laravel.com/1.x/stacks/inertia.html#custom-rendering "Laravel Jetstream Interia Custom Rendering.")
[^3]: [Laravel Jetstream Interia Form / Validation Helpers](https://jetstream.laravel.com/1.x/stacks/inertia.html#form-validation-helpers "Laravel Jetstream Interia Form / Validation Helpers.")

