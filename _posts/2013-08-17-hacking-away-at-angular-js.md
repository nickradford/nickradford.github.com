---
layout: post
title: 'Hacking Away at Angular.js'
date: 2013-08-17
tags: angular.js, javascript
---

Some recent research at work has led me to [Angular.js][angular]. Angular is a full featured, client-side, web application framework from the good guys over at Google.

---

### Discaimer

This is my first *real* foray into blogging, and it's going to be very rough for a while. I'm doing this more for me, as explaining how something works is a great way to learn it yourself. Please excuse the wall of text as I find my voice and writing style.

This post is meant to be a collection of thoughts surrounding my initial findings with Angular.

---

![Angular.js][angular-img]

Altogether the framework is very powerful. It offers:

* Two-way data binding
* Declarative control structures
* Reusable components through directives
* High testability by removing reliance on the DOM from controllers

Since my work lives in the [presentation tier][wiki-presentation-tier], I'm going to be dealing mostly with directives. [Directives][ng-directive] are the mechanism by which Angular allows you to 'extend' HTML to support custom behaviors and elements.. 

Angular comes with some directives already defined, like `ng-repeat` and `ng-click`. The pre-defined directives are easy to spot, as they're all prefixed with `ng-`. The directives defined by Angular are --mostly-- behaviors, they add some behavior to the DOM element they're attached to.

Fair warning -- if you're new to Angular, there's a LOT to unwrap in the following Gist, but I'll do my best.

{% gist 6246692 %}

The `<body>` has an `ng-app` attribute on it, which tells Angular to run in the body. The `ng-controller` attribute on the `<ul>` tells Angular that the **PostsController** will provide the scope for any child elements of the unordered list.

On the list item, we see two attributes: `ng-repeat` and `ng-click`. `ng-repeat` will clones the `<li>` for each `post in posts` defined on the `$scope` by the `PostsController`, and the `ng-click` registers the click handler for when that DOM element is clicked. The click handler is also defined on the `$scope` by the controller.

After the `ng-click`, you'll see {% raw %}`{{title}}`{% endraw %}, which is how we interpolate strings in Angular. 

The `PostsController` gets passed a `$scope` object. This is how you can expose variables to be used in the rendering of the page.

What's really great here is that to render additional posts, all that needs to change is the `$scope`'s post attribute. Once that happens, the DOM will automatically update to show the added posts. Say goodbye to jQuery-spaghetti / heavy DOM manipulation code, and say hello to declarative views and insulated controllers which don't need to understand the view.

Next time I'll be writing about reusable components using Angular.js. Feel free to leave me some love <sup>(or hate... however you feel)</sup> in the comments below.

[angular]: http://angularjs.org
[angular-img]: /images/angularjs.png

[ng-directive]: http://docs.angularjs.org/guide/directive

[wiki-presentation-tier]: http://en.wikipedia.org/wiki/Multitier_architecture#Three-tier_architecture