## That's no moon - pros and cons of mimicking vs integration testing against a real endpoint

As mentioned, we had lots of fun writing test fixtures for most of our endpoints (all of them in fact)

For some of them we even went as far as writing elaborate scripts and switches to modify it slightly, to test different results.

The alternative was to test against a pseudo live system that broke 60% of our tests every time someone meddled around with it, keeping us firefighting fake forest fires.

Mimicking our endpoints really made it easier.

But does it show the real state of the system?
What if the data you're receiving is broken but the tests wont detect that because you're only testing against a mock?

Are we better of just letting it hit the real endpoint and fixing when it crashes?

My suggestion is no. Endpoints should be tested in a different manner, or on a seriously limited scale. If you insist, make one, or two tests, and let the suites be different, so you keep them separately from most of your "real" tests.
