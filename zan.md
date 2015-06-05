* Retrospective of new testing developments from Google I/O - News from the Rebel base (We are obviously not sure what that is going to be before I/O in May)
* Current options for Android Testing - How to bullseye a womp rat
* Unit Testing on the JVM vs Roboelectric - Even R2 makes mistakes
* A look at the pros and cons of Calabash - The Empire's secret weapon
* BDD using Cucumber JVM with Activity Instrumentation Testing - "Search your feelings, father! You can do this"
* Pros and Cons of mimicking and integration testing with a real endpoint - "Thats no moon! It's a space station!"
* Efficient testing - "How to make your CI run in less than 12 parsecs"

## Current options
Android applications, or mobile in general, has historically lacked decent testing support.

Well, some testing support has been around since the early days of API level 1. But that was seriously limited, emulators were a pile of turd and nothing worked. Good luck with that.

### Robolectric

So a while a go we got Robolectric. Combined with a major shift from ANT to Maven in terms of build tools, it appeared that a normal human being can actually *script* builds without selling their soul to the devil. A good thing, definitely.

So for a long long time, Robolectric was the weapon of choice for the more civilised defenders of the galaxy. It allowed for testing in hyperspace, no emulators required, as all tests ran directly on your local JVM space station.

But it had a dark side as well, quite literally. Robolectric is made possible by having a 'shadow' implementation of android.jar, effectively faking all framework methods and providing an alternative implementation. Any changes to android framework needed to be reflected by them.

### AndroidTest strikes back

At the same time as the rebel alliance on Github developed Robolectric, the imperial forces of Google scrambled and made several improvements to official testing support that made Android testing on the Emulator not that bad.

They announced Android Studio, our beloved IntelliJ based IDE that came with a brand new build system, gradle. Instead of *scripting* in XML you could write your build script in groovy, a proper scripting language.

Around that time they also revealed HAXM, a kernel extension for Intel x86 processors that greatly sped up and stabilised the emulator.

Aided by the band of mercenaries from the Genymotion system, we now had 2 decent and stable emulators to choose from.

Suddenly, running tests became a reasonably nice experience. After installing the both apk files on the device the tests ran quickly. For a while, we did most of our "unit" tests against the emulator/genymotion, even on the CI, without the need for Robolectric.

### Testing hits light speed

Earlier this year, after a couple of teasers at Droidcon London and GTAC, Google empire finally released proper unit testing support. Blazingly fast, on the JVM it quickly became our favourite weapon.

Without the need to package an apk and install it on a device, you can run hundreds of tests in seconds.

Google does this using a mocked android.jar. The tradeoff being that if the code you're testing touches any android framework components it'll throw an exception.

There is an option to make them all return default values, which can help if you absolutely need to hit any android specific methods, but it's best to just avoid it. Wrap the logger in an interface and all is fine in the world.

### Tie fighter vs X-wing

In a battle between 2 main testing frameworks, there is no real winner. Both have advantages and drawbacks of their own, so it's clearly a combat between pilots doing the actual coding and testing.

Robolectric:
 - allows to unit test activities, services on jvm
 - not supported by google, had some trouble integrating with gradle builds in the past
 - large development community based on github, contributors include the legendary Jedi Master Jake Wharton.

'android' test:
 - not as complete as robolectric - best works with pojos
 - natively supported by the google empire, some great people working on it full time
 - google code.
 - it's documented by google. Ever tried using volley?

At M&S we don't use robolectric. Most of our unit tests are testing POJOs, so shadow classes really aren't necessary. We make much effort in mocking our dependencies so it works well for us.
