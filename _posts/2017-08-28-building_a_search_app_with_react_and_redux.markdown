---
layout: post
title:  "Building A Search App With React and Redux"
date:   2017-08-28 06:49:00 +0000
---


In the modern web users expect applications that load quickly, navigate to different resources without a reload and perform complicated tasks in the background without any disruption to the experience. People no longer want to click on a link and wait for the new page to load, they want it to simply appear. There are many ways to accomplish this objective and one such way is by using the React Javascript library along with the Redux middleware. React was originally created by Facebook and is now maintained by Facebook, Instagram and individuals worldwide. It allows for the creation of large scale web applications that do not require a refresh when the content changes. There are some innovative new features that React brought to the public, including: 

* Virtual DOM: A cache of the document object model that React checks for changes and only renders updates to the actual DOM when changes are present.
* Properties: Immutable values that flow to a component and are rendered in HTML.
* JSX: The incorporation of the ability to add full HTML syntax within the Javascript body, which according to the design makes for cleaner code, although some developers find the usage of JSX messy.

In addition, a useful library to supplement a React application with is Redux. This middleware helps to maintain the application's state, which is the collection of data that the website is based on. It is the state that React checks in its Virtual DOM for changes that need to be rendered. The state is critical to a React application and thus should only minimally be manipulated directly. Redux helps manage the application's state by passing changes through a reducer that uses actions to assign new objects to state, rather than setting the state directly. It contributes greatly towards consistent behavior in applications and also comes with some great testing suites that developers can use in browser to help with production.

As my fifth portfolio project for the Flatiron School, I built a React application with Redux middleware for people searching for  jobs in the tech sector. The project, **techMap()**, is built on a Rails backend with React and Redux serving as the frontend. It incorporates the Google custom search API to facilitate web searching. When a user first visits the site, React loads the initial state with data from a predefined Google search. This initial state is set with only React and does not use Redux, since it is never manipulated with after its initial load and does not need the additional middleware. 

> ![](http://i.imgur.com/5t5iK7m.png)

The user has a large search box on the top of the page, which they can use to search for jobs with any keywords they choose. The search function sends the user input to the Rails backend, which sends the request to the Google custom search API. The React frontend receives the data and converts it first to JSON and then, with the help of Redux middleware, adds it to the state, which causes an automatic rerender of the page without any page refreshing or reloading. React will take the data received and format it to only show the title of the search listing, the first sentence of the content and only the first page of listings so as to reduce clutter for the user. Each time a user searches the Redux middleware updates the state and React rerenders the page. 

The repository for techMap() can be found on [Github](https://github.com/benhayehudi/techMap_v_010).
