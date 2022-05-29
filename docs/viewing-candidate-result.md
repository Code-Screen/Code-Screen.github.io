# Viewing Results

Once we have completed our analysis of a candidate's solution for one of your tests (which usually takes roughly 10 minutes from when the candidate submits their solution), we will send you an email stating whether the candidate passed or failed the test. This email will also contain a link to view more details
about the result.

**Note** that if you have integrated CodeScreen with your `Applicant Tracking System (ATS)`, then you will also receive an email
from them. 

We also allow you to customize how you want to be notified when a result is ready. Read [here](notification-preferences.md) for more details.

Once you click into the result, you will see a screen that is similiar to the following:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 90%;" src="codescreenResult.png" alt="Result"/>
</figure>

<br>

This screen is broken into the following sections:

### Unit Test Cases Result

In the top left, you can see the number of unit test cases that passed and failed when we ran them against the candidate's
submission. You can also view more details on the failing test cases, which contains a summary of the percentage of passing tests
cases for each test suite and the individual failure message for each failing test case.

### Code Coverage Result
Below the unit test cases summary, we show the code coverage results. This is the percentage of the candidate's code that is covered by unit test cases.<br><br>
**Note** that we allow the candidate to add their own unit test cases. These are included in the final run of the candidate's
submission and contribute to the code coverage result.

### Issues

In the top right of the screen, we show the results of our static code analysis of the candidate's code.
The goal of this analysis is to reveal issues with the candidate's code such as code smells, bad design patterns, etc.

We do this to help you speed up the process of reviewing a submission, and make this workflow as close as possible to how you review
your colleagues' code internally.

Once you click on one of the issue rows, you will be brought to the corresponding line of code on `GitHub`.

**Note** we only include the issues that we find in the files that the candidate added/edited.

### Test Run Output

This section gives you access to the full output log file that was generated when we built the candidate's submission (compiled the code, ran the unit test cases, etc.).

### Time Taken

The amount of time it took the candidate to complete the test.

### Github Repo

A link to the candidate's code on `GitHub`.

### GitHub Unified Diff

A link to view all changes/additions between the initial commit and the candidate's last commit (i.e. before any hidden tests were added). This helps speed up the review process as you can view the candidate's solution in its entirety rather than on a per commit basis.

### Request Changes

We provide a workflow that allows you to easily give candidates a "second shot" at the test.
Click [here](request-improvements-on-candidates-result.md) for more details.

### Give Feedback

We also provide a nice workflow that enables you to give feedback to a candidate on their solution.
Click [here](giving-feedback-to-candidates.md) for more details.



