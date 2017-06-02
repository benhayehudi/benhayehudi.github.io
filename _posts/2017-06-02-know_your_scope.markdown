---
layout: post
title:  Know Your Scope
date:   2017-06-02 16:27:59 +0000
---


During my time as a rabbi one of the most important questions I would ask people to consider who met with me for advice on a pressing personal problem was their particular vantage point or perspective. How does this seemingly intractable conflict with your spouse, colleague, neighbor or friend look like from the other perspective? What would a disinterested observer note about the dilemma that you, as someone deeply invested in it, cannot currently see? This practice of imagining different perspectives would often help people reassess the challenge or inter-personal conflict and create the space to conceive of new framings and new solutions. 

To know the perch upon which you sit is vital for good relationship buiding, whether in the office or in the home. Understanding your scope gives you vital perspective about both the possibilities and the limits. 

![](https://i.ytimg.com/vi/KCvNZ0CaWEk/hqdefault.jpg)

To know your scope in programming is also very important. Let's say you are building a multi-faceted program in object oriented Ruby and you have some Classes with multiple methods defined in each. You are working with data in Arrays and Hashes and often converting Hashes into Arrays to utilize the data. The data, in all of its continually changing and varied forms, is being assigned to variables for manipulation by the program. With each variable you assign you need to ask the fundamental question: Do you know the scope of this variable?

* Local variables, often intialized with just a lowercase letter, live in the place where they began. If it is within a method that is where they will stay. Attempting to call that variable in another method will produce an error.

* A variable beginning with a "@" will exist in every instance of a class. That variable will be accessible to each instantiation of a class. For example, if you wanted every instance of a Class Person to puts "Good morning!" you could do that with an @instance variable. 

* Any variable beginning with a "@@" lives within the entirety of a class. It can be accessed inside and outside any method within that class. The primary difference between a @@class and @instance variable is that the instance variable lives within the local instantiation specifically, so if you change the value in one instance it only impacts that instance. 

* Next, are the $global variables, whose scope is the entire Ruby program. These are not advisable to use since they can not only be accessed from anywhere in the program, they can also be changed from anywhere in the program, which makes debugging later on quite difficult. 

* Lastly, are the CONSTANTS. They do as their name makes it sound. Once they are defined their value remains the same and should not be altered. They are great if you know that data will always need to be the same. CONSTANTS are interesting in that their scope depends on where they are defined. If they are defined in a class they are available in that class, if they are defined outside of a specific class they are given a global scope.

What do you want your variable to do? Who do you want to access it? How do you want it to be used in your program? These are essential questions in the design of an efficient and elegant program, in Ruby or in any other language. Just as you need to know your scope in an inter-personal conflict or office issue, it is important to know the scope of your variables.

Perhaps we can create a Ten Commandments of programming and if we do, one of the top ones will be: **Know Your Scope**.




