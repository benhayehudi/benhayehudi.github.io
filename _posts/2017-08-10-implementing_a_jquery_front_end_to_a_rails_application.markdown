---
layout: post
title:  "Implementing a jQuery Front End To A Rails Application"
date:   2017-08-10 11:09:50 +0000
---


It is hard to believe, but after an exciting and challenging past couple months I am now prepared to submit my fourth out of five portfolio projects. The requirement for this project was to expand upon our previous Ruby on Rails application by refactoring the front-end with jQuery and a JSON API. I went into this project assuming that it would be relatively simple, after all I already had a fully functioning application and all I needed to do was adjust the front-end, how hard could that be? 

Throughout the process I learned how hard indeed it could be to refactor an existing application with a new front-end. First of all, the beauty of jQuery is that from the user experience, they never leave the page that they started on. The user clicks on a link or submits a form and without a refresh the new content is right where it should be. From the developer perspective, that happens because the processes have been moved to behind the scenes asynchronously so the user's browser is not frozen by the request. However, this presents a challenge when loading content from the database based on parameters present in the link. If the link is not actually "clicked," how do those parameters get to the Rails controller and then, ultimately, to the view? After doing a lot of research, it became clear that this is a common issue. I was able to successfully build for it by fetching the XHR request in the Rails controller and selecting the parameter I needed from that XHR request. 

Additionally, since a page refresh does not happen, how do you transition the user experience to a single page view, instead of multiple pages? This, too, is not an uncommon problem, but it was a new problem for me. A quick solution to this issue rested with using CSS styling to hide the later content within divs and then, within the Javascript code, resetting the CSS styling to make it visible when the user requests it. 

Overall, building a front-end with jQuery presents the user with a faster experience, especially if there is a very large database or a lot of content to load. Yet, there is something unsatisfying from the developer perspective. If an objective of good programming is to be efficient in our code, it felt inefficient to need to define each necessary action in jQuery as to how it interacted with the DOM. In the next part of the curriculum I will be learning React, which I believe addresses this issue to a large extent.

You can view the project on [Github](https://github.com/benhayehudi/parental_v_020).
