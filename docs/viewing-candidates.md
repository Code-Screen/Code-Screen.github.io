# Viewing Candidates

When you click into an assessment from the home screen, you will see a table containing all the candidates you have sent the assessment to.

This table is broken into three different sections:

`In Progress` - Candidates who have been sent the assessment but have not yet started/finished.

`Passed` - Candidates who have passed the assessment.

`Failed` - Candidates who have failed the assessment.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 80%;" src="inProgress.png" alt="Send assessment 3"/>
</figure>

<br>

An [Activity Log](viewing-activity-log.md) is available for each candidate, which provides a real-time overview of how a candidate is progressing through your assessment.

### In Progress

In the In Progress section, the `Time Left` initially shows how long the candidate has to start the assessment (based on the Deadline value for your assessment). Once a candidate starts their assessment, it shows how long they have to complete the assessment (based on the Time Limit value for your assessment). 

There is also a `Last Event` column showing which step each candidate is at when taking one of your assessments. The full list of event types are given below:

- `Sent Email`
- `Opened Email`
- `Clicked Email`
- `Started`
- `Pushed First Commit`
- `Completed`
- `Changes Requested`
- `Opened Request Changes Email`
- `Clicked Request Changes Email`
- `Addressing Comments`
- `Email Bounced`

### Passed and Failed

Both the `Passed` and `Failed` sections will contain a `Score` field, which is calculated as the number of passing unit tests ÷ number of total unit tests, given as a percentage. You can also sort the candidates by score.

The Failed section will also contain a `Reason` field, which will either be `unit tests` or `Expired`.

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 80%;" src="failedSection.png" alt="Send assessment 3"/>
</figure>

You can then click the [See Report](viewing-candidate-report.md) button which will bring you to a screen containing the full report we generated for the candidate.
