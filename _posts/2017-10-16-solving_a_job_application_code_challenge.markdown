---
layout: post
title:      "Solving a Job Application Code Challenge"
date:       2017-10-16 16:13:01 +0000
permalink:  solving_a_job_application_code_challenge
---


As I discussed in an [earlier post](https://dev.to/benhayehudi/beginning-the-coding-job-search), I recently graduated from the Flatiron School's online immersive full stack bootcamp. For the past few weeks I have been involved in trying to find work that is nested within the triple formula of work I love, work I am good at and work where I could make a meaningful impact. Thankfully, I have discovered that this industry is abundant in opportunities to contribute to exciting endeavors that seek to impact people's lives for the better, whether that is about efficiency, communication, financial planning and many more areas. 

One of the integral parts of the interview process is demonstrating your technical skillset to prospective employers. This part of the interview process can be terrifying for recent bootcamp grads, especially *liberal arts programmers* (*a term I coined for people who come to coding from a non-math or non-science background*). For this week's installment of coding concepts for liberal arts programmers we are going to break down a code challenge presented in a real job application.

This is the challenge:


> Sort the characters in the following string:

> `abcdefghijklmnopqrstuvwxyz_`

> by the number of times the character appears in the following text (descending):

> ...

> Now take the sorted string, and drop all the characters after (and including) the  _. The remaining word is the answer.

I did not include the very long string of text in the quote above for the sake of brevity. It was a very long string of text. 

The challenge does not specify a language to solve this challenge with, so we are going to do it with Javascript. Why Javascript? It is an incredibly popular language used for all sorts of roles and showing some proficiency with it is an asset in an application. 

The first thing we are going to do is create a new function that will `.reduce()` our very long string of text. (Wait, we were given a `string`, not an `array`, how we will use `.reduce()` on that? We'll get there.) What does `.reduce()` do? According to the [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=b), `.reduce()` does the following:

> The reduce() method applies a function against an accumulator and each element in the array (from left to right) to reduce it to a single value. 

We want to use `.reduce()` simply because it will calculate for us the total for the number of times each of the characters appear in the long string of text. So let's do it:

```
function findTheWord(array) {
  let newArray = array.reduce((total, char) => {
    if (total[char] === undefined) {
      total[char] = 0;
     }
    total[char] += 1
    return total
  }, {}); 
```

What did we do here?

First, we created a new variable `newArray` to hold the result of our `.reduce()` action. Then we first check to see if the value is `undefined` and if so we assign it a value of 0. Otherwise, for each time we encounter that character we increment by 1. Finally, we `return` the `total` as an object containing key-value pairs. 

Now that we have an object list of each letter with how many times it appears, what do we do next? Well, the challenge says that it needs to be in *descending order*, thus let's do that:

```
...

let descendingOrder = Object.keys(newArray).sort((a, b) => newArray[b] - newArray[a])
```

Here we create a new variable called `descendingOrder`, which will organize the contents of our object keys (the characters) according to descending order by providing an argument to the `.sort()` function of sorting by `newArray[b] - newArray[a]`.

The last step is to `return` what we arrived at with only the characters before and up to, but not including the "_" character. We will do that with a `.slice()`, specifying where we want to start from and where we want to end:

```
...

return descendingOrder.slice(0, descendingOrder.indexOf("_")).join('');

```

In this action we only return the value of `descendingOrder` from the first index point until we reach the "_" character. The `.join()` method [joins all elements of an array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) into a string, which we need to do here because, if you remember, we somehow turned that initial long string into an array in order to do what we did with it. 

Our function in its entirety now looks like this:

```
function findTheWord(array) {
  let newArray = array.reduce((total, char) => {
    if (total[char] === undefined) {
      total[char] = 0;
     }
    total[char] += 1
    return total
  }, {}); 
  let descendingOrder = Object.keys(newArray).sort((a, b) => newArray[b] - newArray[a])
  return descendingOrder.slice(0, descendingOrder.indexOf("_")).join('');
}
```

In order to convert our long string of characters into an array we simply just need to turn it into an array first before running our new function, so something like this:

```
let array = Array.from(longString);
findTheWord(array);
// returns the word hidden in that long string of initial characters
```

That concludes our walkthrough of a way to solve that application challenge. The great part about coding is there are so many ways to accomplish anything. Please let me know how you would solve this challenge!  
