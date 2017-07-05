---
layout: post
title:  "Introducing Yom Kef: Your Fun Day In Israel!"
date:   2017-07-05 18:36:09 +0000
---


After creating and recreating activity spreadsheets for each time my family and I traveled to Israel, I knew it was time for something better. I needed a way to easily save my favorite things to do and discover new things for the next trip. This application needed to be easy to use and allow me to organize activities by age appropriate category, because even if you're going to Israel with your kids, it's nice to have a date night! Out of this need, [Yom Kef](http://yomkef.fun) was born.

[Yom Kef](http://yomkef.fun), which means "fun day" in Hebrew, is entirely user generated and crowd sourced. There are many ways to find things to do in Israel, but there is something extra special about knowing someone took the time to add the listing her or himself, because it really was that great of an experience. When you go to Israel on a trip your time is limited and you want to make sure that what you are thinking of doing was recommended by someone who has been there, done it and loved it. 

The application was coded in Ruby and Sinatra using a PostgreSQL database and ActiveRecord. The front-end of the site is based on Bootstrap and the customized fonts come from Google Fonts. It is modeled on the MVC (Models, Views and Controllers) structure with two controllers, two models and view routes defined in the controllers for all the functions of the program and roughly follows the Sinatra RESTful Routes structure. 

When you first visit Yom Kef you are greeted by a welcome page that shares some information about the application and invites you to either sign up, login, browse activity listings or add a listing (registration required to add listings). 

![](http://i.imgur.com/CMExChi.png)

You can easily view all the listings by heading over to the All Listings page and from there, once logged in, you can add any listing to your personal profile.

![](http://i.imgur.com/khaEHP8.png)

Did you have a great experience somewhere in Israel? Don't see it in the current listings, then you can easily add it yourself at the Add Listing page. Once you do so it will automatically be part of your profile's activities and be viewable by all the other members so that they can also add it to their profiles.

![](http://i.imgur.com/eLLIsfI.png)

Planning your next trip to Israel and want to check out all the activities you added to your profile? Just view My Listings and never again do you need to start from scratch in planning your next trip!

![](http://i.imgur.com/BjBIuvM.png)

The source code can be found on [GitHub](https://github.com/benhayehudi/yomkef) and the application can be accessed at http://yomkef.fun.


