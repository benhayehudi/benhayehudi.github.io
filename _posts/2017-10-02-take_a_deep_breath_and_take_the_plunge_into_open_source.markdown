---
layout: post
title:  "Take A Deep Breath And Take The Plunge Into Open Source"
date:   2017-10-02 12:54:32 +0000
---


You have created your own projects, both the frontend and the backend. You feel comfortable coding, writing documentation and debugging. Yet, the thought of going into someone else's Github repository and making a pull request feels absolutely daunting. What if I submit something that has bugs? What if I make a big mistake? What if I simply don't do it right? The nightmare of countless doomsday "What if...?" scenarios fill your mind. You pause and walk away from the idea. 

Don't let this be you! This was me for a bit as I pondered getting involved in any open source project. I would look longingly at the contributions being made to projects on Github and wanted to be a part of it. Yet, I felt like I was not ready to do so. The problem with that thinking is when would I ever be ready? However, with the encouragement of the month long [Hacktoberfest](https://hacktoberfest.digitalocean.com/), I decided to finally take the plunge. 

If you're like me and feel nervous about taking your code public into an open source project, I hope this post will help you take the plunge also. First thing first, how do you even get started?

Once you have identified an open source project you want to contribute to (*and a great way to start this month is find one with the label [`hacktoberfest`](https://github.com/search?q=label:hacktoberfest+state:open+type:issue)*) fork a copy to your Github account. You can do that by simply clicking on the `fork` link on the top righthand corner of the repository page:

![A Github Fork Link](https://i.imgur.com/obC186a.png)

After you have forked a copy of the repository to your own account, you will be redirected to your copy of it where you can click on the `clone` link, which will copy into your clipboard the url of the repository:

![A Github Clone Link](https://i.imgur.com/SSFDDK9.png)

From your terminal go ahead and type `git clone` and paste the content of your clipboard, which will be the url. You now have a local copy of the open source project on your computer and any edits you commit will be saved on your own copy on your Github account. In other words, you can get to work on making your contribution without worrying that you will push something up to the main project that is not ready.

Skip ahead a few hours (*or a few days!*) and you are now ready to formally contribute to the open source project. How do you do that? This is also a lot simpler than you might think. First, go back to the main Github repository of the open source project and find the button for `New pull request`:

![A Github Pull Request Link](https://i.imgur.com/zV0nMsn.png)

Once you click that link you will see the following:

![A Github Compare Across Forks Link](https://i.imgur.com/bPeFyU7.png)

Click on the link for `compare across forks` and this will let you make a pull request from your forked copy. Choose your repository from the dropdown list on the righthand side. Github will then compare the code in both the master repository and in yours and, if there is any difference, will present you with a simple form to complete a pull request. The form is self-explanatory. Just remember to document well what you did to help the project owners understand your contribution.

Now, what kind of contributions can you make? 

Open source projects have requests for all sorts of contributions. If you feel like you want to just dip your toes in the water before jumping in the deep end (*which is what I did!*) find a project that needs help with its documentation. Helping to either write or edit a project's documentation is a great way to get to know the code of a project, because you have to understand how it works before you can write any documentation well and lets you make a meaningful contribution. Then, once you have done that and you now see that there are no bloodthirsty sharks in the water waiting to attack on the first sniff of a newbie contributor, go ahead think what could be your next step. Maybe it is making a further contribution to that project in a part of the code that you feel confident in or finding another project and doing that there. 

I am a firm believer in incremental progress. I believe that is how we make sustainable growth. Thus, if you start with a documentation contribution then move on to a small code edit in an area you feel good about and then move on to something else where it takes you a bit more brainwork to figure out and keep on doing that. Before you know it, you will be a regular contributor to the open source community and making a positive impact on code used by developers around the world. 

Sounds awesome, right? So let's get started! 
