## BDD using Cucumber JVM with Activity Instrumentation Testing - "Search your feelings, father! You can do this"

Zan Skywalker has already told you about how he successfully used the calabash weapon to prevent the empires fines bug squadron from infraltating his code base.  I too used that technique once, in fact it is the very technique that has left me stuck in this slimy mudhole.  I had visions of the impending destruction of the Jedi order and decided to retreat to a world that did not exist, yet a planet writing with living force.

The problem with Calabash is the way that it sits as think layer on top of the UI, this means you only have indirect control over the elements, kind of like a virtual finger poking your app.  Because of this interface your tests can run very slowly and it is not possible (easily anyay) to start a journey mid way through so every story starts at the initialization point.  Soon you nice clean functional test suite start to take days to run so you invest time to parallel run the events.  This works for a while and then you find the latest android SDK breaks calabash and you either can't upgrade till calabash does or you have no functional tests till it catches up.

Reveal to you my secrets I will, 

There are two benefits to using Calabash, one is the functional testing and the other is the interface that the Gherkin DSL describing your behavior give you to the business.

Google have you covered with the functional testing, you can use the Activity Instrumentation Test Case and the Espresso framework to deliver this functionality with the additional benefit of being able to interface direct into the activities and code under test.  Espresso has come along way and version 2.2 works just fine with the new AndroidJUnitRunner and Android Studio.  Espresso does not really do anything so clever it just provides automatic syncronisation of test actions so you never have to write dozens of wait cases between executing an action and asserting state.

Now the BDD part well you can write BDD in the code there is nothing stopping you expressing behavior as part of the names of your test methods however it looks pretty ugly and good luck trying to get a wookie to read it, it is more likely to rip your arms off.  There may be a solution, CucumberJVM is a pure java implementation of the popular test runner built in ruby.  It allows you to express your behaviour in the Gherkin DSL then execute your unit tests, there are a few learnings such as how to effectively structure your tests but so far the results look very positive.

Now please excuse me I am going to club that kid over the head with my stick, steal his x-wing and head back to the fleet.
