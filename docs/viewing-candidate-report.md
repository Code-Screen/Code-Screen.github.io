# Viewing Candidate Report

Once we have completed our analysis of a candidate's solution for one of your assessments (which usually takes roughly 10 minutes from when the candidate submits their solution), we will send you an email stating whether the candidate passed or failed the assessment. This email will also contain a link to view a detailed
report about our analysis.

**Note** that if you have integrated CodeScreen with your `Applicant Tracking System (ATS)`, then you will also receive an email from them. 

We also allow you to customize how you want to be notified when a result is ready. Read [here](notification-preferences.md) for more details.

Once you click into the report, you will see a screen that is similiar to the following:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 90%;" src="codescreenResult.png" alt="Result"/>
</figure>

<br>

This screen is broken into the following sections:

### Unit Test Cases Result

In the top left, you can see the number of unit test cases that passed and failed when we ran them against the candidate's
submission. You can also view more details on the failing test cases, which contains a summary of the percentage of passing assessments
cases for each assessment suite and the individual failure message for each failing assessment case.

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

The amount of time it took the candidate to complete the assessment.

### Plagiarism Check Passed

The result of our plagiarism check for this solution. A green tick means that no similarities to all previous solutions for this assessment have been detected. A red X means we have found enough similarities with another solution that warrants further investigation. We also provide a link to review the comparisons further.

### Github Repo

A link to the candidate's code on `GitHub`.

### GitHub Unified Diff

A link to view all changes/additions between the initial commit and the candidate's last commit (i.e. before any hidden unit tests were added). This helps speed up the review process as you can view the candidate's solution in its entirety rather than on a per commit basis.

### Request Changes

We provide a workflow that allows you to easily give candidates a "second shot" at the assessment.
Click [here](request-improvements-on-candidates-result.md) for more details.

### Give Feedback

We also provide a nice workflow that enables you to give feedback to a candidate on their solution.
Click [here](giving-feedback-to-candidates.md) for more details.
