# Editing Email Templates

Candidates receieve multiple emails from CodeScreen during their journey through a CodeScreen test, from when they
are initially sent a test to when they submit their solution.

We provide the option to edit these email templates to include your company's logo and wording, which gives the candidate
more of a consistent experience across your interview process.

To edit the email templates, click into the
<a href="https://app.codescreen.dev/#/client-templates" target="_blank">Emails</a> section on the top toolbar on CodeScreen, which will take you to the following screen:

<figure>
  <figcaption style="font-style: italic;"></figcaption>
  </br>
  <img style="max-width: 60%;" src="templates.png" alt="Test Choice"/>
</figure>

Each email type has a default template associated with it, and you can view these by clicking `Show default` beside each type.

To edit an email template, click `Edit`. You can then edit the default `HTML` to include your own branding and wording.
Editing HTML can be easily performed by you or by one of your developer colleagues if you are a non-technical user. If this is not an option, then please message on our live chat and we can do this for you.

Each email template has a set of `substitution variables` that we use to dynamically insert information into the email HTML.<br>
Examples of these includes the candidate's first name, the test time limit, etc.

Below is a table which shows at which point during the candidate test journey lifecycle each email is sent, and the
substitution variables that are used for each:

<table>
<thead>
<tr>
<td style="white-space: nowrap;"><strong>Email name</strong></td><td><strong>Sent point</strong></td><td><strong> Variables used</strong></td></tr>
</thead><tbody>
<tr>
<td>Begin Test</td><td>When a candidate is initially sent the test.</td><td>{firstName}, {testTitle}, {companyName}, {candidateLinkUrl},
{timeToCompleteTestSentDisplayValue}, {timeToCompleteTestBeginsDisplayValue}.</td></tr>
<tr>
<td>Test Details</td><td>When a candidate begins the test.</td><td>{testTitle}, {companyName}, {candidateLinkUrl}, {repoUrl}.</td></tr>
<tr>
<td>First Commit Pushed</td><td>When a candidate pushes their first commit(s) to their GitHub repo.</td><td>{testTitle}, {companyName}, {candidateLinkUrl}.</td></tr>
<td>Expiry Warning</td><td>Sent when there is 30 minutes left before the test expires.</td><td>{firstName}, {testTitle}, {companyName}, {candidateLinkUrl}.</td></tr>
<td>Acknowledgement</td><td>Sent after the candidates submits their solution for the test.</td><td>{testTitle}, {companyName}.</td></tr>
<td>Feedback</td><td>Sent to notify the candidate that you have given them feedback on their solution.</td><td>{testTitle}, {companyName}, {repoUrl}.</td></tr>
</tbody></table>

An explanation on what each variable is referring to is provided below:

* `{firstName}` - The candidate's first name.

* `{testTitle}` - The name of your test that the candidate has been sent.
* `{companyName}` - The name of your company you set when you signed up to CodeScreen. 
* `{candidateLinkUrl}` - The link to the candidate's test page on CodeScreen.
* `{repoUrl}` - The link to the candidate's private repo on GitHub. This can be edited <a href="https://app.codescreen.dev/#/client-profile-edit/details" target="_blank">here</a>.
* `{timeToCompleteTestSentDisplayValue}` - The number of days the candidate has to complete the test from when they are <br> sent the test, e.g. "1 day", "2 days", etc.
* `{timeToCompleteTestBeginsDisplayValue}` - The number of hours/days the candidate has to complete the test from when they <br> begin the test, e.g. "3 hours", "1 day", etc.

### Editing the From Email Address

You can also edit the email address from which the above emails are sent. The default email address is
<a href="mailto:hello@codescreen.dev">hello@codescreen.dev</a>. 

If you want to change this to one of your internal email addresses you use for hiring, just enter it into the
`From Email Address` field, and click the `Save` button.

Once you do this, you will receive a verification request email from <a href="https://aws.amazon.com/ses/" target="_blank">Amazon SES</a>,
our email provider. You just need to click the link in that email, and then we will be able to send emails from the email address you added!
