---
layout: post
title:  "Formatting Is Not Just For Newbies ![](http://i.imgur.com/V8gGUWv.png)"
date:   2017-07-18 19:49:45 +0000
---


After two months in the immersive online web development program at the [Flatiron School](https://flatironschool.com/) I am very much in the midst of learning Ruby on Rails. First, I learned both Procedural and Object Oriented Ruby then I learned HTML, CSS, SQL, ActiveRecord and Sinatra. I completed two final projects. One project is published at [Ruby Gems](https://rubygems.org/gems/rzman) and the other one has been successfully deployed to Heroku with a [custom domain name](http://www.yomkef.fun/) and a PostgreSQL databas utilizing the BCrypt Ruby gem to allow for the creation of secure user accounts. 

I started off this journey in web development knowing very little about coding and, two months later, I genuinely feel like I can actually do this. When beginning in the program it is easy to feel a bit of what has been called *imposter syndrome*. Am I really learning or just mimicking the instructions? However, it is through the creation of the final projects, which are programs you create entirely from scratch, that empower you in your own developing skillset. 

All of this is to say that I felt pretty confident about going into my second final project assessment on my Ruby on Sinatra program, *[Yom Kef](https://github.com/benhayehudi/yomkef-flatiron)*. The program worked, and that is the most important thing, right?

Well, I learned another important lesson today thanks to my assessment instructor, [Luke Ghenco](https://github.com/Lukeghenco). As we reviewed the code together, which consisted of multiple controllers and models with numerous routes and many view pages it became clear that without proper formatting it was just plain difficult for a newcomer to the program code to make out what it was supposed to do. Furthermore, as we refactored the code it is inevitable for bugs to pop up when making changes and without proper formatting it became even more difficult to debug.

What do I mean by proper formatting? Let's say you have a view page that has more than 150 lines of code and the code looks like this:

> <% @listings.uniq.each do |listing| %>
> < div class="col-md-12 item-listing">
> < img src="<% if listing.img_url == nil || listing.img_url == "" %><%= "/images/default_listing_img.png" %><% else %><%= listing.img_url %><% end %>" class="img-thumbnail" alt="Yom Kef" align="left" width="120"><% end %>

There is some complicated ERB syntax in that snippet. While it is certainly possible to parse what it is doing, imagine having that formatting repeat itself numerous times for hundreds of lines of code and with even more interpolated Ruby in the HTML?

If that same snippet of code is broken up into its natural parts and indented appropriately, it becomes not only easier for someone new to the code to understand it, but for even the original developer to debug when bugs appear. 

After my assessment on my Sinatra project, I went back to my code and reformatted every file to reflect proper indentation, spacing and line breaks. Doing so took a little while, but the effort was well worthwhile.
