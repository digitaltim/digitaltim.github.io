---
layout: post
title: "Learning Laravel Jetstream - Intertia - Vue - Part 1"
date: 2020-11-30
---

I decided to dive into a new project based on [Laravel Jetstream](https://jetstream.laravel.com/1.x/introduction.html "Laravel Jetstream is a beautifully designed application scaffolding for Laravel."). Going down that route I also ended up choosing the Interia/Vue path. Basically, I get Vue.js on the front end, Laravel on the back, Intertia.js as the routing glue to use Laravel's routes. All of this is styled with Tailwind CSS. So I'm trying to learn all of these at the same time. I've dabbled in the past with Laravel and built a front end using Vue via the component library Bootstrap Vue. Slight learning curve...

I went through the Tailwind CSS Tutorial Series[^1]. I feel more comfortable with it now... Yet I have all of these Jetstream Vue components that I'm not sure if I should use. As I'm looking around the code, I sense that I can probably reuse a bit more than I initially thought I could. But I don't know how to exactly. That's what prompted me to write this post. I need to work out my understanding....

I have a bunch of components that "feel" deeply nested. It's a little tough to keep track of them and understand intuitively how they all fit together. I'm going to run through a small example...

I have this parent container/component:

- resources\js\Layouts\AppLayout.vue

This mainly has the navbar (which is a bit complex), slots for header and main content and then a portal for a modal. This is, as the name implies, the base layout for the applicaiton.

AppLayout.vue is used by other components. A good example is 'resources\js\Pages\Profile\Show.vue' as this contains several other components.  In the template section of this component the AppLayout component wraps everything. The '<template #header>' section is populated with a simple h2. Then the rest of the content goes into the main slot.

The main slot contains several other components: UpdateProfileInformationForm, UpdatePasswordForm, TwoFactorAuthenticationForm, LogoutOtherBrowserSessionsForm and DeleteUserForm. The TwoFactorAuthenticationForm is wrapped in a v-if conditional '<div v-if="$page.jetstream.canManageTwoFactorAuthentication">'. I think $page is an instance variable... Though I don't see it documented anywhere...

I like the idea that these components live as single files. They are displayed in a page and some have some minimal styling added to them through additional Tailwind utility classes where used. But if you go into just one of those components, say 'resources\js\Pages\Profile\UpdateProfileInformationForm.vue' you'll find this component is comprised of it's own set of components. It has it's own overall layout template: JetFormSection. This has template sections where content is added. It even takes a method when a submission happens with '@submitted="updateProfileInformation"'. This is a little tricky but when you look at 'resources\js\Jetstream\FormSection.vue', you'll see a form element that wraps the 'form' slot and overrides the default submit event with '<form @submit.prevent="$emit('submitted')">'.

Even this element has a nested child component: JetSectionTitle. This might be the simplest component as it's just a template: 'resources\js\Jetstream\SectionTitle.vue'. It has two slots: title and description.

What stands out to me with following the trail of nested components, is that they all seems to sort of have their own styling but it fits into the larger style of the application. I'm left wondering if I should try to reuse these components or create a set of my own. I don't think there's a clear answer because I don't yet fully know what my application will look like. At least this gives me a somewhat clear example of how to scaffold a sufficiently complex project.

A 'page' is located in it's own folder in resources\js\Pages. Each page could contain several components which are comprised of the base components and likely have the layout in one master component which sources the other components. This top level page is typically called Show.vue. The base components are located in resources\js\Components. The overall application layout is in resources\js\Layouts. 

Data appears to be passed into the component a couple of ways. I see some props being passed to Show.vue. I also see $page instance var. I need to figure this out... I see some of the routes I created have an associative array passed in: '['responseData' => SkidCost::all()]'. This is accessed in the vue component via '$page.responseData'. I also see some route model binding going on... It's almost as if the props are set positionally from the route. So maybe it doesn't matter what they're named. Also, I'm a little confused by the route 'profile.show'. It seems like this is part of Laravel Fortify service provider...

Overall there are lots of moving pieces and several learning curves in this project. I have to jump around the documentation and reference many things. Right now I'm trying to lay out my interface. So I'm mainly in Vue/Tailwind. Yet I need to hydrate those views with data from the DB. So that puts me back into Laravel land. But in order to have a route, I need to utilitze Intertia. Having a good understanding of how these pieces fit together, what features are enabled in Laravel especially and how to extend the base scaffolded project is kind of daunting. I just need to chip away at it.

[^1]: [Tailwind CSS Tutorial](https://www.youtube.com/watch?v=bxmDnn7lrnk&list=PL4cUxeGkcC9gpXORlEHjc5bgnIi5HEGhw "Tailwind CSS Tutorial.")

