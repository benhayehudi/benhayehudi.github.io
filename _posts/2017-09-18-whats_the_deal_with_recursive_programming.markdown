---
layout: post
title:  "What's The Deal With Recursive Programming?"
date:   2017-09-18 14:09:13 +0000
---


Linked lists. Binary searches. Depth first searches. Recursion. If you are like me and came to coding not with a math or scientific background these concepts can seem overwhelming at first. You may be really good at making awesome web apps and problem solving, but the same tools you have used intuitively, when referenced with technical names can fly over the top of your head. Over the next few weeks I will write short posts that introduce these concepts to people, who like me, might be referred to as a "liberal arts" or "humanities" programmers. We begin with recursive programming.

What is recursion? 

[Wikipedia](https://en.wikipedia.org/wiki/Recursion_(computer_science) defines recursion in computer science as:

> Recursion in computer science is a method where the solution to a problem depends on solutions to smaller instances of the same problem (as opposed to iteration). The approach can be applied to many types of problems, and recursion is one of the central ideas of computer science.

What does that mean in simple terms? Essentially, if the problem you are trying to solve can be broken down into a lot of smaller steps that follow one another, you can use recursion to arrive at the solution. Recursive programming has the benefit (*although not always*) of being more time efficient than an iterative approach and can be helpful when working with very large sets of data.

Let's take a simple problem and break it down with a recursive approach. How would we build a program to check if a given string is a palindrome? (Refresher: A palindrome is any word that reads the same backward or forward.) 

One recursive solution to our palindrome function would be the following:


```
function isPalindrome(myString) {
    if (myString.length <= 1) return true;
    if (myString.charAt(0) != myString.charAt(myString.length - 1)) return false;
    return isPalindrome(myString.substr(1, myString.length - 2)); 
}
``` 
As you can see in line 4 of our `isPalindrome` function we are returning the function itself from within the function. That is recursion in a nutshell. Why are we doing this? Line by line examination will make that clear. 

Line 1: 
`if (myString.length <= 1) return true;`
Here we are checking to see if the string we have passed is 1 character (or less). If it is, then obviously a 1 character word can be read the same backward or forward and the program returns `true`. 

Line 2: 
` if (myString.charAt(0) != myString.charAt(myString.length - 1)) return false;`
On this line we perform the next check. If the first letter of the string does not match the last letter of the string that would be a quick way to determine that the string is certainly not a palindrome and then the program returns `false`. 

Line 3:
`return isPalindrome(myString.substr(1, myString.length -2));`
This is where the heart of our recursion lies. How do we implement a palindrome check? By going through each letter and checking to see if the complementary letter at the opposite place in the index of that string matches. We start that process on line 2 by checking the first and last letters. We could then build out line by line a check for each letter in the string, but that seems (and is) inefficient. Rather, we call the function itself to continue by going through lines 1-2 repeatedly until it arrives at the final letter. 

If at any point 
```
myString.charAt(0) 
// 0 being the current beginning letter 
// after the previous beginning letter was removed with .substr()
``` 
does not equal the current ending letter then the program will return false. But if it goes through all the letters in the string and each time it returns `true` then we know we have a palindrome. 

That in a nutshell is recursive programming. 
