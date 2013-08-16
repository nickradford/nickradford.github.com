---
layout: post
title: 'Hacking Away at Angular.js'
date: 2013-08-16
tags: angular.js, javascript
---

Some recent research at work has led me to [Angular.js][angular]. Angular is a full featured, client-side, web application framework from the good guys over at Google.

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

[angular]: http://angularjs.org
[angular-img]: /images/angularjs.png

[ng-directive]: http://docs.angularjs.org/guide/directive

[wiki-presentation-tier]: http://en.wikipedia.org/wiki/Multitier_architecture#Three-tier_architecture