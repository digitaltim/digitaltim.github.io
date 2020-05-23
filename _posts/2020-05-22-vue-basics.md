---
layout: post
title: "Vue Basics"
date: 2020-05-22
---

Vue is a progressive web framework for building user interfaces. Meaning that it can be incorporated into a project incrementally. This is because the core library focusses on the view layer whereas adding additional tooling/libraries turns it into a more fully featured framework.

## Declarative Rendering[^1]
Calling a function to change a DOM element is imperative rendering. In Vue you declare how an element is derived from state and props, thus declarative rendering[^2]. One of the ways to do this is with template syntax which links the data variables defined in Vue to the placeholders in the template. Using {% raw %} `{{ <variable name> }}` {% endraw %} causes text interpolation[^3]. Using the `v-bind:` directive allows binding values to an element's attributes. The `v-` prefix indicates a Vue directive. 

## Conditionals and Loops[^4]
Vue uses the conditional directive `v-if` to bind data to the structure of the DOM. The `v-for` directive can be used to iterate through a data source declared in Vue.

## Handling User Input[^5]
Vue uses the `v-on` directive to attach event listens to elements. These listeners can then invoke methods defined in the Vue object to manipulate state. The `v-model` directive creates two way data binding between form input and state.

## Composing with Components[^6]
Applications can be abstracted and broken down into smaller chunks called components. One huge benefit is components are self contained and thus mostly reusable. A component in it's simiplest form is a Vue definition, instantiated with preset options. Components can be included in another component's template using composition creating a parent/child relationship. Parents can customize the state of children by passing a set of properties (called props in Vue) into it. The example in the reference shows the inherent power and simplicity of combining this pattern using the directives `v-for` to loop through the parent's data source and `v-bind` to pass this data into instances of the child components created through the props interface.

## Wrapping Up
The concepts presented are simple on the surface and easily understandable. Yet taking this patterns and applying it to my project still is somewhat elusive. I'll need to start small and iterate to reinforce the basics and manage the inevitable complexity to come.

**Note**: I had to modify this post to properly display curly braces.[^7]

[^1]: [Vue Declarative Rendering](https://vuejs.org/v2/guide/index.html#Declarative-Rendering)
[^2]: [The philosophy of React: Declarative rendering](https://fjorgedigital.com/insights/blog/the-philosophy-of-react-declarative-rendering/)
[^3]: [String interpolation](https://en.wikipedia.org/wiki/String_interpolation)
[^4]: [Vue Conditionals and Loops](https://vuejs.org/v2/guide/index.html#Conditionals-and-Loops)
[^5]: [Vue Handling User Input](https://vuejs.org/v2/guide/index.html#Handling-User-Input)
[^6]: [Vue Composing with Components](https://vuejs.org/v2/guide/index.html#Composing-with-Components)
[^7]: [Escaping double curly braces inside a markdown code block in Jekyll](https://stackoverflow.com/questions/24102498/escaping-double-curly-braces-inside-a-markdown-code-block-in-jekyll)
