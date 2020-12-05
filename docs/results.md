# Viewing Results

Once we have completed our analysis of a candidate's submission for one of your tests, we will send you an email
stating whether the candidate passed or failed the test. This email will also contain a link to view more details
about the result.

**Note** that if you have integrated CodeScreen with your `Applicant Tracking System (ATS)`, then you will also receive an email
from them.

Once you click into the result, you will see a screen that is similiar to the following:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 70%;" src="codeScreenResult.png" alt="Result"/>
</figure>

This screen is broken into the following sections:

### Unit Test Cases Result

In the top left, you can see the number of unit test cases that passed and failed when we ran them against the candidate's
submission. You can also view the details of each failing test case.

### Code Coverage Result
Below the unit test cases summary, we show the code coverage results. This is the percentage of the candidate's code that is covered by unit test cases.<br>
**Note** that we allow the candidate to add their own unit test cases. These are included in the final run of the candidate's
submission and contribute to the code coverage result, but are not included in the unit test score for the candidate.

### Issues

In the top right of the screen, we show the results of our static code analysis of the candidate's code.
The goal of this analysis is to reveal issues with the candidate's code such as code smells, bad design patterns, etc.

We do this to help you speed up the process of reviewing a submission, and make this workflow as close as possible to how you review
your colleagues' code internally.

### Test Run Output

This section gives you access to the full output log file that was generated when we built the candidate's submission (compiled the code, ran the unit test cases, etc.).

### Time Taken

The amount of time it took the candidate to complete the test.

### Github Repo

A link to the candidate's code on `GitHub`.

### Request Changes

We provide a workflow that allows you to easily give candidates a "second shot" at the test.
Click [here](improvements.md) for more details.

### Give Feedback

We also provide a nice workflow that enables you to give feedback to a candidate on their solution.
Click [here](feedback.md) for more details.



