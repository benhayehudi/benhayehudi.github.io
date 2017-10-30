---
layout: post
title:      "A Brief Introduction to REST APIs"
date:       2017-10-30 15:12:30 +0000
permalink:  a_brief_introduction_to_rest_apis
---

Even if you have no idea what REST means, you have been interacting with it throughout the web for quite some time. Now let's take some time to explore what REST means and what a REST API is. REST stands for "REpresentational State Transfer". The concept was introduced to the world in a 2000 doctoral dissertation by Roy Fielding. REST is a way of managing the client-server relationship and strives for speed and performance by incorporating re-usable components. What are the basic features of a RESTful architecture:

1. Stateless: Client data is not stored on the server between interactions and the session is stored client-side (typically in session storage). 
2. Client<->Server: There is a separation of concerns between the frontend (client) and the backend (server). They operate independently of each other and both are replaceable. 
3. Cache: Data from the server can be cached on the client, which can improve performance speed.

In addition to these three fundamental features of REST, there is also a uniform approach to the composition of base URLs. This allows for a standardization of service, which prior to the introduction of REST, did not exist. For example, a `GET` request to `/dogs`, should yield all the dogs in the database, whereas a `GET` request to `/dogs/5` would render the dog with an ID of 5. Similarly, REST utilizes standard methods like `GET`, `PUT`, `DELETE` and `POST` to perform actions. 

Thus, a RESTful API would be one that is a) stateless, b) separates concerns between client-server, c) allows caching of data client-side and d) utilizes standardized base URLs and standardized methods to perform actions to manipulate, add or delete data. 

Furthermore, it has become common practice for REST APIs to also return data in a standard format. The most popular format nowadays is JSON (JavaScript Object Notation). The standardization of the formatting of the data is another step towards uniformity in the way resources are interacted with on the web allowing for developers to solve problems and not spend their time in configuration of the basic architecture. 

When requesting data from an API you might get back something like this:

```
{
    title: "This is JSON",
    content: [
        chapter: "1",
        page: "200",
        firstParagraph: "This is what JSON looks like when it is returned from an API."
    ],
    author: "Ben Greenberg",
    source: "thecodingrabbi.com"
}
```

This allows for easy access of that data within the JSON with something like `data.title`, which would return "This is JSON".

Where can you find RESTful APIs? Everywhere! [Twitter](https://dev.twitter.com/twitterkit/android/access-rest-api). [Google](https://developers.google.com/drive/v2/reference/). [Ebay](https://go.developer.ebay.com/api-documentation). So many of the popular services we take advantage of daily utilize a RESTful architecture for their API service. Now you can also. 

