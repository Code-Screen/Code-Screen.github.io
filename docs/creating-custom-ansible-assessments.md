# Creating Custom Ansible Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.</br>

You can then add the description of your assessment, choose <strong>Ansible</strong> from the drop-down list of available `DevOps` tools, and set the time limit for the assessment.</br>

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.
This repository will simply contain an `Ansible .gitignore` file and a README containing the description of the assessment that you added during the setup.<br><br>
We leave it up to you to decide your assessment's directory layout etc.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Ansible assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="ansibleRepo.png" alt="Ansible Repo"/>
</figure>

</br></br>

You can then update this repository with details of your `Ansible` assessment and start sending the assessment to candidates.

### Automated test-suite setup
Automated test-suite scoring for `Ansible` is not currently supported.
