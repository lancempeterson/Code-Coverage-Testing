# Optimized Code Testing using Modified Condition Decision Coverage

As a software testing engineer I wrote Python scripts to test aviation software, and successfully applied modified condition decision coverage (MC/DC) to optimize our test suite. By utilizing MC/DC, I was able to determine the minimum required test cases, and reduce the total number of test cases from exponential to linear. This greatly improved the efficiency and time complexity of our testing process, resulting in faster and more effective testing of the software.

Modified Condition Decision Coverage (MC/DC) is a software testing technique used to ensure that each condition in a logical expression is independently tested. This technique is commonly used in safety-critical applications, such as aviation software, where failures can have severe consequences.

To achieve MC/DC coverage, each condition in the logical expression must be independently varied and tested in combination with all other conditions. This ensures that the test suite covers all possible combinations of the conditions, and can identify any faults or errors in the logic.

Suppose we have a software requirement that specifies the following condition: "The system should issue an alert if the plane's altitude is less than 1000 feet AND either the speed is greater than 500 knots or the fuel level is less than 10%."

We can express this requirement using the logical expression "A && (B || C)", where:

A represents the condition "plane's altitude is less than 1000 feet"
B represents the condition "speed is greater than 500 knots"
C represents the condition "fuel level is less than 10%"

MC/DC requires that 'Each condition in a decision has been shown to independently affect that decision's outcome'. To achieve MC/DC coverage for this logical expression, we select a minimum set of test cases that cover each condition independently.

For example, the following test cases satisfy the MC/DC coverage criteria:

A is true, B is true, C is false
A is true, B is false, C is true
A is true, B is false, C is false
A is false, B is true, C is false

In real software, the above logical expression and the requirements would be expressed using actual programming constructs. For example, the following lines of Python code would implement the above requirement:

```python
if altitude < 1000 and (speed > 500 or fuel < 0.1):
    issue_alert()
```

This code would evaluate the logical expression "altitude < 1000 and (speed > 500 or fuel < 0.1)" and issue an alert if the result is true, in accordance with the software requirement. By applying MC/DC coverage, we can ensure that this code is properly tested and any potential errors are identified before the software is deployed.

For any requirement there will always be a total of 2^N possible test cases for N number of conditions. In this example there are 8 total test cases. Using MC/DC we can remove redundant tests that do not need to be included, and still achieve proper test coverage.

As the number of conditions to test increases, so does the amount of testing required. Performing Multiple Condition Coverage (MCC) would necessitate twice the number of tests as MC/DC. In practice, many projects commonly involve decisions with 16 or more conditions.

Consider evaluating coverage for a decision with 16 conditions:

MCC tests required: 2^16 = 65,536.
MC/DC tests required: 16 + 1 = 17.
MC/DC reduces the number of required tests by 65,519.

Using MC/DC we can reduce the total number of test cases from exponential to linear. I was able to use this technique to great effect, which resulted in faster and more efficent testing of the software.
