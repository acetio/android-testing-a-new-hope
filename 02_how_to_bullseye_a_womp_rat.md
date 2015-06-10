# Current options for Android Testing - How to bullseye a womp rat
When you have to attack a space station the size of a moon you need a pretty special plan.  Thankfully the schematics that R2 brought back after they escaped with their lives show that even something as deadly as the Death Star has a weakness.

Looking at these schematic we need to change our plan of attack.  We do not need huge fire from an MC80 star cruiser but targeted fire in the exhaust ports from our smaller ships.  As the cockey Zan Skywalker pointed out that this is in fact quite easy, he regularly used to bullseye womp rats in his T17 and a womp rat is no bigger than a star destroyer exhaust port.

Ok so how do we do this, we need two waves of attack, we are going to send in the fast ships our X-Wings first these are much more capable at avoiding the tie fighters then we will send in the B-Wing heavy assault fighters as they may be slower but cause damage over a larger area.

First the X-Wing assault operation Unit Test, we are going to look at
* JUnit 3
* JUnit 4

The basis of a unit test attack is to hit fast and often, this of course means that we can only take on one single tie fighter at any one time but this is very effective as X-Wings in a JUnit formation should do most of our damage.

Up until recently in Android we have only really had JUnit3 test but with the 1.0 release we have the capability to use JUnit4.  A unit test is a single logical function in our code and all the unit tests run independent of one another.  In some instances we need to manage our dependencies, the empire is never going to make our work easy but thanks to modern programming patterns like dependency injection which are prevalent across this galaxy we should be able to make light work of this.  JUnit4 is merely an update on our tried and tested JUnit3 strategy however it does bring us a more semantic way to write our test code with the addition of annotations like @Before instead of having to override setUp methods.  We also have the benefit of using these annotations to ignore test methods and the ability to set a timeout on the duration of a test.

That will cover most of our attack however we still need to use our B-Wings to attack the surface of the Death Star.  We should never underestimate the damage a surface mounted turret can do and we need to take these out too.

There are various methods to perform this attack we have.
* The Activity Instrumentation Formation
* The Calabash Attack
* The less popular Selendroid death dive
* Robotium
* JVM based testing

These attacks require a little more detail so I will hand you over to Zan Skywalker who will continue this breifing.
