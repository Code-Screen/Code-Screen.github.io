# Creating Custom Ansible Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Ansible</strong> from the drop-down list of available `DevOps` tools, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will simply contain an `Ansible .gitignore` file and a README containing the description of the test that you added during the setup.<br><br>
We leave it up to you to decide your assessment's directory layout etc.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Ansible assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="ansibleRepo.png" alt="Angular Repo"/>
</figure>

</br></br>

You can then update this repository with details of your `Ansible` assessment and start sending the test to candidates.

### Automated test-suite setup
Automated test-suite scoring for `Ansible` is not currently supported.
