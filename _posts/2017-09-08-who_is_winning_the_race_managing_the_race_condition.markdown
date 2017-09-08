---
layout: post
title:  "Who Is Winning The Race? Managing The Race Condition"
date:   2017-09-08 14:29:43 +0000
---


You have setup a beautiful web application that fetches data from an API. Your ReactJS frontend updates state with the data it receives from the API and rerenders the component with the new information. The API sends back to you an array of items, so naturally you have some simple iterator function to go through the array and render each item. Your syntax is written well. You can watch your app make the fetch request and receive the data. You see that your state gets updated with the new data. Yet, no matter what you do your app returns an error that it can't `map()` over undefined. What does that mean? Why is that happening?

Welcome to one of the most common problems in modern web development. It can be called many things, but it is typically referred to as the race condition. Javascript runs things in the order that it receives them and will not wait for one item to finish before going on to the next item. In our example we might have the following code:

```
fetch('/api/awesomeListOfThings/', request)
      .then(data => data.json())
      .then(data => this.setState({ myAwesomeState: data }))
```

Then we'll want to iterate over the data with something perhaps like this:

```
this.state.myAwesomeState.map(coolStuff =>
        <RenderCard coolStuff={coolStuff} key={coolStuff.id} />)
```

This should work fine, except for the fact that our program is not going to patiently wait for the fetch to finish before moving on to the next step. While the fetch is still happening our program wants to start iterating over myAwesomeState. But, there is nothing in myAwesomeState yet! That is precisely the problem the race condition describes. 

How might we address this problem? One simple way to solve this issue is keep our application busy with something else while the fetch request is still working. This also provides a benefit to our users who will now know that their favorite app did not just break, but simply the information they want is still loading. We can do that by creating a new object in state that defaults to `false` before the fetch finishes and `true` when it is done and then use that to set a conditional statement in our render:

```
fetch('/api/awesomeListOfThings/', request)
      .then(data => data.json())
      .then(data => this.setState({ 
			    myAwesomeState: data,
					finishedLoading: true 
			}))
```

```
this.state.finishedLoading?
    this.state.myAwesomeState.map(coolStuff =>
        <RenderCard coolStuff={coolStuff} key={coolStuff.id} />)
:
    "All your awesome information is still loading, please hang on..."
```

First we check to see if `finishedLoading` is `true`, which will only happen once the fetch request finishes. If it is `true` then we go ahead and iterate over the data that we now have in our possession. If it is not `true` we display a friendly message to our users to hold on while the API request is still processing. Once `finishedLoading` updates in state to `true` then the first part of our condition will be implemented and we will no longer experience the error that we cannot `.map()` over undefined. 

Now that we solved that issue for our hypothetical web application, we can take a deep breath... and then move on to the other myriad issues we need to resolve. Coding is, after all, 5% writing new code and 95% problem solving and debugging!
