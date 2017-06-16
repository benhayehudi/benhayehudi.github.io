---
layout: post
title:  "Introducing RZman: Ruby Zmanim CLI Gem"
date:   2017-06-16 00:12:39 -0400
---


It's Friday afternoon and you are rushing to finish the last of your chores before שבת (*Shabbat*, the Jewish Sabbath) begins. In the midst of the rushing you stop and wonder how much time do you *really* have before candle lighting? It's Tuesday and the workday is a grind. Is it too early to pray מנחה, the afternoon service? Is it too late?

*If only there was an easy way to check both of these things from your command line in Ruby. *

**Now there is with [RZman](https://github.com/benhayehudi/rzman/), the Ruby Zmanim gem!**

[RZman](https://github.com/benhayehudi/rzman) is a CLI (command line interface) Ruby application that will provide you with the זמנים, the daily prayer times and Shabbat candle lighting times customized for you based on your zipcode. Let's take a walk through of the program. Follow along in the [YouTube video](https://www.youtube.com/watch?v=6UT_QlbfKqU):

<iframe width="853" height="480" src="https://www.youtube.com/embed/6UT_QlbfKqU" frameborder="0" allowfullscreen></iframe>

When you first run [RZman](https://github.com/benhayehudi/rzman) you will encounter the main menu:

![](http://i.imgur.com/JUQTJmI.png)

If you wish to get the prayer times for the day simply enter "1" at the prompt, followed by your zipcode at the next prompt. Once you do so you will get the following:

![](http://i.imgur.com/CN4G6yO.png)

As you can see a selection of times are provided in an easy to read format based on your zipcode scraped from MyZmanim.com. You are then asked if you wish to go back to the main menu or if you would like to exit the program.

However, if what you wanted was the candle lighting time for this coming Shabbat instead of entering "1" at the main menu all you needed to do was enter "2", followed by your zipcode and then you would see this:

![](http://i.imgur.com/og8VYXR.png)

After receiving your candle lighting time, scraped from MyJewishLearning.com, you are asked if you would prefer returning to the main menu or exiting the program.

[RZman](https://github.com/benhayehudi/rzman) is a simple and compact solution for those in a hurry looking to get the relevant times. 

*How does it work?*

The [RZman](https://github.com/benhayehudi/rzman) gem relies on scraping two different websites to obtain the relevant data. It utilizes the existing [Nokogiri](http://www.nokogiri.org/) and [OpenURI](https://ruby-doc.org/stdlib-2.1.0/libdoc/open-uri/rdoc/OpenURI.html) gems to get the webpages and then to search through them using the appropriate CSS selectors. It stores the information into an array of hashes and then iterates over that array for each :key => :value pair. It also includes a simple zipcode validator method, #zip_valid? that checks to make sure the user input for a zipcode consisted of five numerical digits. If not, it will ask the user to start again. 

[RZman](https://github.com/benhayehudi/rzman) can be found on Github. 

Happy *davening* and *Shabbat Shalom*!

[RZman](https://github.com/benhayehudi/rzman) now available on [RubyGems.org](https://rubygems.org/gems/rzman).


