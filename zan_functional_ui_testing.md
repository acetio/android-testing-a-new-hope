## Empire's secret weapons

Once upon a time ancient spacefarers realised that galaxy was a big place and our tiny x wings and tie fighters weren't going to cut it.

That's when we started constructing big elaborate starships and space stations to help us control the vast expanse of space. (And produce awesome space explosions completely unrelated to laws of physics)

That's why superweapons like UI Automator, Robotium, Espresso and Calabash were born.

They allow for a different kind of testing, something we call end to end or functional testing.

In essence, you are scripting your app and telling it what buttons to poke and what output to expect.

### The fleet

Ways of doing this differ from tool to tool, here is a brief overview of each one:

UI Automator is the heavy hitting star destroyer of the imperial fleet - it works directly on the android system, has access to settings, app drawer and your app. You use it for black box style tests with elaborate setup.

Robotium, Selendroid and similar tools are the heavy cruisers of the rebellion. are open source alternatives to UI automator, that allow scripting for only your application, but they also allow for slightly more isolated tests, not hitting the real apis, but injecting mocked endpoints using tools such as wiremock, or mimic.

Calabash is a fancy looking cruiser, a love child of robotium and cucumber, allowing you to write BDD style given when then test scenarios and defining your tests in ruby which then execute on the device. We are heavy users of calabash, on both ios and android teams at M&S, because it's seemingly a perfect combination of business readability and developer efficiency.
Of course such a fancy high tech contraption has its weaknesses, we'll check more on that in a minute.  

Espresso is the newest most technologically advanced corvette in the fleet of Google Empire. It's super efficient and capable of devastating attacks.
It's also probably the most low level of the functional alternatives, tying neatly among other androidTest test cases.

### Calabash

As mentioned, calabash is great as it joins the fairyland of business with the real world - that is, of us developers.

We can define features in gherkin, usually in cooperation with our product owner and then write our tests to match that acceptance criteria.

We can then integrate that nicely with Xamarin Test Cloud to run our acceptance tests on the cloud on as many devices as we want.

So we write and write our tests and suddenly end up with 100-200 bdd style tests that take 3 hours to run.

Samples of scenarios covered:
- I correctly login
- I incorrectly login
- press login with no password
- press login with no username
- press login with invalid username

These run every. single. time. It's super easy to overdo calabashing, because it's so convenient. We must not fall into that trap.

(Insert It's a trap Akbar!)

Hard to run them on a bog standard emulator, allegedly good things coming in near future that improve the emulators a lot.

Haxm helps. So does genymotion but good luck starting that thing on any kind of VM.  (Apparently it's possible to improve it if you're into kernel hacking)

HTTPAliveDisconnected happens too many times. Solution is only to kill ruby, adb, and keep retrying. Sometimes ritual slaughter of small mammals also helps.

Timeouts are shit.

Mocking web services is a ball ache. Wiremock could be better. We are using mimic to mock them. Xamarin tests run against a heroku instance with our setup.
Fragile and flaky as hell at the moment.

### Espresso

Espresso is clever. It's main two selling points are a fluid api based on hamcrest matchers and clever idle detection that enables your test steps to proceed as quickly as items are presented on the screen and animations have ended.

Pain points:
Starting Espresso tests on a mature project - migrating tests from calabash.
Dependencies in AndroidTest aren't much fun.


### Food for thought

Calabash without the ruby.

Calabash is built on top of Robotium and Cucumber.

What if we could write cucumber tests and implement them not in ruby, but in native java instead?

Currently experimenting with a way to use Cucumber JVM in conjunction with Espresso for a "calabash effect". Would work nicely on a bog standard emulator, even on Travis CI (or jenkins).

Suppose we want to keep a few of our "normal" instrumentation tests, you can play around with build types to pick a runner for each build type / flavour combination.

Initial experiments were promising, working on them in my spare time.
