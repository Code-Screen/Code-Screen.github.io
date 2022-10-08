# Creating Custom Terraform Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Terraform</strong> from the drop-down list of available `DevOps` tools, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Terraform</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Terraform assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="terraform_repo.png" alt="Terraform Repo"/>
</figure>

</br>

<figure>
  <figcaption style="font-style: italic;">The terraform directory in the GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="terraform_repo_dir.png" alt="Terraform Repo"/>
</figure>

</br>

### Automated test-suite setup

If you would like to add assessments that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these to the existing `foo_assessment.go` file in the template repository. It would be best if you also renamed this `foo_assessment.go` file to something more relevant to your assessment.

We use the [Terraassessment](https://terraassessment.gruntwork.io/) `Go` library to run automated assessments against the resources that are created when we run & deploy the candidate's Terraform code.

For custom assessments, the candidate's Terraform code must be deployed to an `AWS` or `GCP` account that belongs to you.

For us to have the permission to deploy to your `AWS` account, you must create an `IAM` user has all the required permissions to create the resources needed to pass your assessment successfully. The `AWS Access Key and Secret Key` for this user needs to be then added to the existing `credentials` file in the template repo.<br>
Likewise, for `GCP`, a service account with all the required permissions must be created in your `GCP` account, and the service account's key `.json` file must be added to the template repo (replacing the existing `foo.json` file).

Note that the candidate's Terraform code must use/be compatible with Terraform version `0.12.25`. This requirement is specified in the `main.tf` file.

You can add more than one unit test files. All unit test file names must end with `_assessment.go`, and all unit test classes with names that end with `_hidden_assessment.go` will not be visible to the candidate. These hidden unit tests allow you to test candidate's solutions against edge cases etc.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.go`, etc.

The existing dependencies and versions in the `go.mod` file must not be modified.
