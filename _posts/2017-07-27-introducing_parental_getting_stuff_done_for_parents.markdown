---
layout: post
title:  "Introducing Parental: Getting Stuff Done for Parents"
date:   2017-07-27 20:21:25 +0000
---


It can be tough being a parent or a caregiver. There is always so many things to remember to do. Did you go grocery shopping? Sign up for the after school activity? Did you get new school supplies? Pick up the dry cleaning? Get those immunization forms completed by the pediatrician? The list goes on and on. 

Parental is an easy to use web application created in Ruby on Rails to help parents and caregivers get stuff done. Parental enables parents and caregivers to create todo lists, add tasks to each todo and experience the great joy of finally marking a specific task or a whole todo as *done*. Users can create an account either through registering on the website or by signing in through Facebook:

> ![](http://i.imgur.com/3WEnsq6.png)

Once a parent or caregiver is logged in they are greeted with a simple question: "What would you like to do?" From this main page a user can add todos and view each individual todo:

> ![](http://i.imgur.com/REDDodB.png)

Each todo has its own display page where it is possible to see where you need to go on a map, get directions, add specific tasks for that todo and mark either specific tasks done or mark the entire todo as done:

> ![](http://i.imgur.com/w67Prsv.png)

The application has three models: Parent, Todo and Task. A parent has many todos through tasks and many tasks. A todo belongs to a parent and has many tasks. A task belongs to both a todo and a parent. Each model has an accompanying controller, which inherits from the ApplicationController. The controllers manage the flow between the models and the user experience (the views) of the program. The task controller, as a subset of a todo, does not have its own index or show views, since a user can only access an individual task through the todo#show view. 

User registration is managed through the BCrypt gem with validations on the Parent class for email and password entries and the utilization of strong params. Facebook signup and login is possible with the Omniauth gem and setup through the Facebook Developers site. A map for each todo is provided through incorporating the Google Maps API and receiving an API key through Google Developers.  Users are persisted with storing an id in the session param and helper methods were created to check for the current user, whether she/he is logged in and whether they are authorized to access the todo they are trying to get.

<iframe width="560" height="315" src="https://www.youtube.com/embed/jylzbyJ-Uzs?showinfo=0" frameborder="0" allowfullscreen></iframe>

The code for Parental can be found on [GitHub](https://github.com/benhayehudi/parental_v_010). 
