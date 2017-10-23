---
layout: post
title:      "What's The Deal with Redux?"
date:       2017-10-23 13:10:05 +0000
permalink:  whats_the_deal_with_redux
---


I have a confession to make. I love working with React. At first, when I started to learn the framework, I found it confusing. It was a big departure from what I had previously worked with in the form of an MVC framework like Ruby on Rails. It was not immediately clear where to start. Where do I put my controllers? What about the models? Why isn't there a clear file structure? However, these questions quickly gave way to an appreciation for the dynamism and flexibility of React. 

While the motto of Rails is *convention over configuration*, meaning you only need to configure the unconventional aspects of your application, with React the entire thing is within your hands to mold and shape accordingly. This, of course, lends itself to be more daunting for the first timer, but eventually becomes empowering.

One aspect of React that is particularly awesome is its handling of `state`. What is state? State is simply the place where your application's data is maintained. A powerful aspect of React is the creation of a Virtual DOM (Document Object Model), which the application checks against for any changes and only re-renders the part of the application where a change occurred. Each React component can have it's own local state and furthermore, state can be passed down from one component to its children components through the use of `props`. 

Yet, as your application grows in complexity, and particularly as you need to maintain common points of data in your state across components, like user information for example, React's component based state starts to become clunky. Then, in 2015, entered Redux. What's the deal with Redux? Simply put, it is the single source of truth for your application.

In other words, Redux helps create a single `store` for all your application's data that is seamlessly shared across the entire breadth of the application. Within Redux a developer uses `reducer` actions that commit changes to the `store`. Each component is only granted access to the elements within the state that the developer deems it needs access to by mapping the Redux state to props within that component. So, for example, you could maintain multiple reducer files organized around different actions within your program (i.e. an API reducer, a search reducer, an authentication reducer, etc.) but ultimately all this data is being handled in a single store: The single source of truth.

When should you implement Redux in your application? This is a source of discussion in the React community. Since Redux is middleware, an additional layer on top of your program (albeit a very small one), some people argue it should only be incorporated when it becomes necessary. That is, when it becomes clear that the various component based states and the piping of data down through components is becoming untenable. While others hold that one should incorporate Redux early on in the development of the application to avoid needing to refactor later. 

I don't have a strong opinion in each way on this discussion. I have built applications that have started without Redux and later went back and incorporated it, and where Redux was incorporated right away, even when it was not obvious it was needed at that stage. I think good early planning, before a single line of code has been committed in an editor, for the development and evolution of a program will shed light for a team on what middleware, including Redux, is necessary for the application. This smart planning is probably better than a strict devotion to any particular Redux orthodoxy of *always* Redux from the beginning or *never* Redux from the beginning. 

There is so much more to learn about both Redux and React and, if you're interested, I recommend you begin by checking out the links below. Once you get started though it may be hard to stop!

**Additional Resources:**
1. [ReactJS](https://reactjs.org/)
2. [React on Github](https://github.com/reactjs)
3. [Redux Usage with React](http://redux.js.org/docs/basics/UsageWithReact.html)
