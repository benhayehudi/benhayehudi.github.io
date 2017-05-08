---
layout: post
title:  "The Eloquence of Abstraction in Ruby and Tosafot"
date:   2017-05-08 18:37:07 +0000
---


During this first week of learning in the online Full Stack Web Development program at the Flatiron School I have studied a lot of Ruby. I have learned about variables, arrays, methods, interpolation, conditions and iteration. Throughout the first week I have applied each new lesson towards the creation of a CLI (command line interface) game of Tic Tac Toe. While creating a Tic Tac Toe game may seem simple it requires a lot to be defined, from the display of an empty board to the ways in which a player could win to knowing whose turn it is and if that move resuted in a win, a draw, the other player's turn or the end of the game.

Throughout this whole process I have delved into the language of Ruby and it is a beautiful language. Previously, I had learned the fundamentals of Javascript and, in comparison, Ruby is simply more coherent and more closely resembles the way we actually speak. This is evident in the way that one can minimize the need to say a lot in order to accomplish a lot. The 1st century Jewish sage [Shammai](https://en.wikipedia.org/wiki/Shammai) summed it up succintly:

> שַׁמַּאי אוֹמֵר... אֱמֹר מְעַט וַעֲשֵׂה הַרְבֵּה, וֶהֱוֵי מְקַבֵּל אֶת כָּל הָאָדָם בְּסֵבֶר פָּנִים יָפוֹת
> 
> Shammai says, "... say little and do much, and receive every person with a pleasant countenance."

[*Sefaria*](https://www.sefaria.org/Pirkei_Avot.1.15?lang=bi&with=all&lang2=en)

In both Javascript and Ruby one can abstract their code to a point where it is clean and minimal, but in Ruby it "receives you with a pleasant contenance." In other words, it is still easy to understand for someone looking at the code for the first time.

For example, if a person wanted to have the computer output a string of text that differed 3 times for each name and age of the person, you could write it like so:

![](http://i63.tinypic.com/68zzw8.png)

In this simple method, #person_age, you have created two arrays, one with the individuals names and one with their ages. You then outputted them, each on a separate line, interpolating a value from the name array and a value from the age array to finish the sentence. It gets the job done but it is tedious to write all that out. What if you wanted to output that for 10 names and ages, or 50 names and ages and not just 3?

Abstracting the code makes it shorter, simpler and more eloquent:

![](http://i64.tinypic.com/2n9yrd3.png)

In this newly created #person_age, the program will iterate through both arrays using the Ruby #zip method and create two new variables, one for each array. The value for each variable will cycle through the array outputting the text we stated until it is complete with both original arrays. It is less tedious and as a result more dynamic than our previous code. We might want to add additional elements to our arrays and, if we do so, we do not need to go back and manually create additional outputs for each new array[x] as we do in our original code. 

While the connection may not be obvious, the quest for eloquence as expressed through abstraction also finds resonance in the classical Talmud commentary, [Tosafot](https://en.wikipedia.org/wiki/Tosafot). A general rule when studying a commentary by Tosafot is the longer it is, the simpler it is to understand, while the shorter the text, the more difficult to understand. This is only partially true. A shorter Tosafot employs abstractions to accomplish the same job that several additional lines of comment would do.

For example, a commentary by Tosafot on the Babylonian Talmud in Tractate Pesahim 101a states clearly:

> דאין קידוש אלא במקום סעודה משום דכתיב וקראת לשבת עונג. כלומר במקום קריאת קידוש שם תהא עונג
> 
> There is no *kiddush* (prayer to sanctify the Sabbath) except in the place of the meal because it is written [in the Biblical text], "And you shall call the Sabbath a delight." That is to say that in the place where you "call" the kiddush, that is the place you should have delight (i.e. your festive meal).

[*Sefaria*](http://www.sefaria.org/Tosafot_on_Pesachim.101a.1.1?lang=bi&with=all&lang2=en)

In this small commentary by the Tosafists, they reference a well known principle, similar to calling a defined #method, that "*d'ayn kiddush aleh be'makom se'udah* -- there is no *kiddush* except in the place of the meal." They do not spend a great deal of time explicating that principle, the simple calling of it is enough to explain what needs to be explained in that moment. A reference is made to a Biblical text, perhaps similar to a readily available library in programming, as a support. In this case, an explanation is required to demonstrate how that Biblical text acts as a support, but once again, that is done succinctly. 

Tosafists shared a similar objective with programmers, which is to keep the text brief and dynamic and to clearly accomplish the job it was meant to accomplish, Often when one encounters a long piece of commentary by the Tosafists, it can be convoluted and its arguments can be harder to follow along. It is in the short pieces that we see their brilliant ability to explain complicated topics quickly and to the point. 

This drive for pleasant, eloquent, dynamic communication lies at the heart of coding. In many ways learning to code is an application of Talmudic discourse to the command line. The Tosafists would be proud.

