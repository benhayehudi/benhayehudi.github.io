---
layout: post
title:      "Merging Arrays in Javascript"
date:       2017-10-09 19:59:31 +0000
permalink:  merging_arrays_in_javascript
---


In my next installment of [coding concepts for liberal arts programmers](https://dev.to/benhayehudi/whats-the-deal-with-binary-search) (*i.e. coders who do not come from a math or science background*) we will look at merging sorted arrays in Javascript. A common challenge you will encounter is the presentation of two arrays of sorted integers and the need to merge them together into one large sorted array. How might you do that? Let's take a look at one method.

In our scenario we have two lists of sorted numbers:

```javascript
let firstList = [4, 6, 8, 9]
let secondList = [2, 3, 5, 7]
```

Before even beginning to code out our solution, if you were facing this problem in any other context what would you do first? Well, you would probably go about creating a new list taking the smallest number from each list and adding it to your new list. How would we code that? At the outset we'd want to just find the smallest number from each list and then remove it so our original lists get smaller and less complicated as we go forward:

```javascript
function getSmallestThenRemove(firstList, secondList) {
    let smallestFirstList = firstList[0];
    let smallestSecondList = secondList[0];

    if (smallestFirstList < smallestSecondList) {
        return firstList.shift()
    } else {
        return secondList.shift()
    }
}
```

In this function we locate the smallest number by referencing the first index place in each existing array and creating two new variables to hold that data. (*In another post we will discuss how to implement a similar function with two unsorted arrays.*) Then we check which smallest number is smaller. If the first list's smallest number is smaller than the second list's smallest number, we return the first list without that number and, if the opposite is true, we return the second list without its smallest number.

Now that we have a function that finds for us the smallest number, removes it from the list and returns the original list without that smallest number, what do we need to do next? 

The next step would be to create another function that calls `getSmallestThenRemove()` from within itself as it iterates through the two separate arrays, adding each smallest number as they are removed from their original arrays into a new merged array:

```javascript
function mergeLists(firstList, secondList) {
    let newList = [];
    let iteratedNum;

    while (firstList.length != 0 && secondList.length != 0) {
        let iteratedNum = getSmallestThenRemove(firstList, secondList)
        newList.push(iteratedNum)
    }
    return newList.concat(firstList).concat(secondList)
}
```

Within the `mergeLists()` function we are doing several things:

1. We create an empty array, which will be the place our new sorted array will live.
2. We create a variable `iteratedNum`, which will hold the current number we are working with.
3. We work our way through the original lists until they are empty (`!= 0`). Each time, we define the value of `iteratedNum` to be the return value of `getSmallestThenRemove()` and push that value into our `newList`.
4. Finally, we return the `newList` by concatenating the remainder of either `firstList` or `secondList`, because once we have worked our way through the function we will be left with one original list that is empty and the other that holds the remainder of our new sorted array.

Thus, returning back to our original two lists, once we run our new function we will return the following:

```javascript
let firstList = [4, 6, 8, 9]
let secondList = [2, 3, 5, 7]

mergeLists(firstList, secondList)

// [2, 3, 4, 5, 6, 7, 8, 9]
```

Check back next week for another installment of coding concepts for liberal arts programmers! 
