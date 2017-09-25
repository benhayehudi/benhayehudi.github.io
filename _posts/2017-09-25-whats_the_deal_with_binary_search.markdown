---
layout: post
title:  "What's The Deal With Binary Search?"
date:   2017-09-25 17:06:35 +0000
---


Last week in my new series of blog posts on programming concepts for *liberal arts* (i.e. you did not come to coding with a science or math background) programmers we discussed [recursive programming](https://dev.to/benhayehudi/whats-the-deal-with-recursive-programming). This week we are going to take a dive into another concept that is likely to come up in a technical interview, which is the binary search algorithm. The term "binary search" has the same effect on a programmer coming from a humanities or liberal arts background as "recursive programming" or even just the word "algorithm," it can cause momentary panic. But, do not panic! The key to figuring it out is to strip it of jargon and break it down into simpler ideas. 

A binary search is a way to go through a group of items quicker than initiating a simple loop if you are dealing with a very large set of data. In fact, this is what you do every time you would open a phone book to search for a record (*remember those huge books left at your doorstep years ago?*). If I asked you to take that enormous phone book and find for me the phone number for a person named John Marcus you would not start from the first page and slowly work your way through the book until you arrived at the "M" section. Rather, you would put your finger on the outside the pages, make an educated guess where the middle of the book was and flip it open there. Then you would assess your current position to make your next move. If you had landed on the "P" records you would know that you went too far and would flip back a few pages. If you had landed on the "K" records you would know that you did not go far enough and would flip forward a few pages.

Why would you intuitively search through a phone book like that? Well, because it is a lot quicker than starting from page one and going page by page! This is exactly what the binary search algorithm is all about. It takes the phone book search and implements it over any array of data.

Let's see it in code:

```
function binarySearch(list, value){
    var first = 0,
        last = list.length - 1,
        middle = Math.floor((last + first)/2);

    while(list[middle] != value && first < last) {
       if (value < list[middle]) {
          last = middle - 1;
        } 
        else if (value > list[middle]) {
          first = middle + 1;
        }
      middle = Math.floor((last + first)/2);
    }
 return (list[middle] != value) ? "not present" : value;
}
```

What are we doing here?

On lines 2-4 we are defining several key variables: `first`, `last` and `middle`. These variables will hold the values for us of the places in the data. We set the `first` variable to the first index item, the `last` variable to the last index item and the `middle` variable we define with a simple math function that gives us the middle of the data set.

On line 6 we set up a `while` condition that looks for two things: 1. The middle value does not equal the value we are searching for and 2. the first item is less than the last item. 

If those are true we then want to know on line 7 if the value we are looking for is less than the middle of the data and, if it is, then we want to reset the `last` variable to equal the end of the middle value. In effect, we are chopping off the second half of the data set because we now know that our value is not there.

However, if the value we are looking for is greater than the middle of the list then we want to reset the `first` variable to be the next item from the middle value on line 9. While on line 11 we are setting the `middle` variable to be once again the middle of the `last` and `first` incorporating the new value for either `last` or `first`.

Lastly, on line 13 we are utilizing a [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator) checking to see if it is `true` that the middle does not equal the value. If the `middle` does equal the `value` then we return the `value` and, if not, we return a simple string telling the user it is not present in the list. 

I hope this was a helpful introduction to the binary search algorithm for the *liberal arts* coder.
