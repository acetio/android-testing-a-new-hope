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
