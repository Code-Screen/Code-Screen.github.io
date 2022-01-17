# Creating Custom PowerShell Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>PowerShell</strong> from the drop-down list of available `DevOps` tools, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will simply contain an `PowerShell .gitignore` file and a README containing the description of the test that you added during the setup.<br><br>
We leave it up to you to decide your assessment's directory layout etc.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom PowerShell assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="powershell_repo.png" alt="PowerShell Repo"/>
</figure>

</br></br>

You can then update this repository with details of your `PowerShell` assessment and start sending the test to candidates.

### Automated test-suite setup
Automated test-suite scoring for `PowerShell` is not currently supported.
