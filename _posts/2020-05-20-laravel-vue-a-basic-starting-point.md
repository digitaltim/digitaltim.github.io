---
layout: post
title: "Laravel Vue a Basic Starting Point"
date: 2020-05-20
---

It's time to jump a little ahead of myself for the sake of getting a default project in place using the stack I'm intending to deploy. My work project is going to be modeled after an existing applicaiton another developer created using Larvel for the backend and Vue.js for the frontend. It's nice that Larvel offers a basic Vue.js scaffolding to get started[^1]. With a couple of commands `composer require laravel/ui:^1.0 --dev` and `php artisan ui vue --auth` my project now has a basic Vue.js frontend.

I also noticed that the composer command specifies to use the 1.0 branch. So I checked out the 7.x documentation[^2] and see it's changed slightly. However, it's interesting to note the underlying laravel/ui repository is now on the 2.x branch[^3]. When I searched for the ui package I also spotted a result from Laracasts that I recalled watching back when I first got started with Laravel[^4]. It touches on the addition of the ui package and how it was factored out of the base Laravel project from the 5.x branch. It's just interesting to note how fast this stuff moves.

Although the prior two commands added basic Vue.js scaffolding to the base project and I can see the changes when I reload the site, the work is not fully finished. When I navigate to the Login or Register pages, there is no styling applied. I needed to run the commands `npm install` and `npm run dev` to install the frontend JavaScript dependencies included with the basic scaffolding and compile the static css and js assets.[^5] Check out the `webpack.mix.js` file to see what's included in this compilation step. It's kind of amazing to think about the implications of what a framework does at this point. Lines of code comes to mind. The finished compiled JavaScript in `public\js\app.js` for this boilerplate application is almost 50k lines long! I can't imagine trying to understand a file this long. That's why modern tooling is so helpful to manage complexity.

Moving along into testing out Vue.js I wanted to add the example component into a template file to test that it works[^6]. I decided to add `<example-component></example-component>` to the `resources\views\auth\login.blade.php` right at the top as the first entry in the `@section('content')` section. It works!

[^1]: [Laravel 6.x JavaScript & CSS Scaffolding](https://laravel.com/docs/6.x/frontend)
[^2]: [Laravel 7.x JavaScript & CSS Scaffolding](https://laravel.com/docs/7.x/frontend)
[^3]: [laravel / ui](https://github.com/laravel/ui)
[^4]: [Frontend Scaffolding Has Been Moved to Laravel UI](https://laracasts.com/series/whats-new-in-laravel-6/episodes/3)
[^5]: [Laravel Writing JavaScript](https://laravel.com/docs/6.x/frontend#writing-javascript)
[^6]: [Laravel Writing Vue Components](https://laravel.com/docs/6.x/frontend#writing-vue-components)

