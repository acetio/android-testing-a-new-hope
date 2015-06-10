# Efficient testing - "How to make your CI run in less than 12 parsecs"

* Balance Risk - DO NOT TEST EVERYTHING
* Consider duplication - Write the appropriate test for the appropriate function. i.e do not test your input validation with 1000 permiatations of a credit card number in a functional test.  Test the class performing the validation at a unit level then test the inputs and outputs at a functional level.
