---
layout: post
title:      "What Happens When Your Tests Fail Intermittently?"
date:       2017-11-27 16:11:10 +0000
permalink:  what_happens_when_your_tests_fail_intermittently
---


![TDD](https://thepracticaldev.s3.amazonaws.com/i/ae50jbdry7gkccqulfp8.png)

One of the many talks I attended at RubyConf 2017 that really grew my approach to development was the one given by [Tim Mertens](https://twitter.com/rockfx01) entitled [*Deterministic Solutions to Intermittent Failures*](http://rubyconf.org/program#session-202). In his talk he walked through defining some approaches one can take and tools one can use when faced with a test that fails only sometimes. Indeed, tests that fail every time are much simpler. It is the test that fails only once in a while that poses the challenge for the developer working in a test driven development environment. Why did it fail this time and not the other time? How do I narrow down the problem(s)? 

The first thing Tim addressed head on in his talk was the "myth of the flaky test". He challenged us to steer away from calling our tests "flaky". A flaky test implies that it is unsolvable. Test code only does exactly what you tell it to do. Instead of flaky, calling it non-deterministic restores our sense of ability to address it. A non-deterministic test failure can eventually be accounted for. If we simply just label the tests that are really bothering us as *flaky* then that might lead us to ignore them and come to also ignore a real issue the test is trying to illuminate for us. 

As mentioned above, tests that fail every time are the best case scenario because they are reproducible. They can be run on your local machine and produce the exact same results. Some common reasons why tests end up failing:

* Stale branches
* Mocked time vs. system time
* Missing preconditions
* Real bugs in your code

**What do you do though when your tests fail intermittently?**

First, try running a subset of your tests from the test suite. Running `rspec` directly is not running a test on a test group, that is your entire test suite. Running `rspect ./spec/test_1` is running a test on a part of your test suite, a test group. When you run your tests, test by test, you can see how each one responds separately and it helps break down the errors for you. 

Sometimes your tests are failing intermittently because of a dependency issue. You can reproduce the order that the tests were run in using `--seed` in RSpec. If you are getting back lots of errors, you might want to narrow down to the first with appending a `--fail-fast` before executing the RSpec test.

Another very powerful tool is the `--bisect` command, which repeatedly divides the set of tests in half until you find the minimal set of tests which cause another test to fail. You can run `--bisect` in collaboration with `--seed` to reproduce the test order and to hone in on exactly the combination of tests that are failing. If `--bisect` succeeds and can show you the exact combination of tests that are causing the failure then you have a case of *test pollution*, which is when one test is causing another test to fail.

**How might you address test pollution?**

A lot of debugging test pollution comes down to lowering your expectations.

To debug a case of test pollution take a look at the data in the tests. Is the data persisting across test examples or the test suite entirely? Your tests should clean up after themselves. However, don't expect them to be pristinely clean! For example, when building the test don't expect `(User.count).to eq(1)` rather expect the action you are testing to change `(User.count).by(1)`.

Similarly, don't expect global scoped items to only return test records. Account for the possibility of other data when you build your tests. On another point, check the caching, specifically around class caching and singleton caching. Reset any cache mutations after any tests that modify them. Yet, also try not to mutate caching in your tests in the first place. Lastly, a great place to check is your constants. Try not to overwrite constants in your test suite.

Perhaps the most common frustration with TDD is wanting to just get on to the next test, or if lucky, pass all of them and move on to the next item. Our desire to make progress though should not come at the expense of spending the time to truly debug the errors in our code. If we do, we may find that those pesky "flaky" tests will come back to get us later in ways that we could have avoided if we only addressed it right away.

You can find the examples Tim used in his talk on [Github](https://github.com/tmertens/intermittent_test_failures).  
