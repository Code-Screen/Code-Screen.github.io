# Creating Custom Vue.js Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Vue</strong> from the drop-down list of available frontend frameworks, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Vue</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Vue assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="vue.png" alt="Vue.js Repo"/>
</figure>

</br></br>

You can then update this repository with details of your Vue assessment and start sending the assessment to candidates.

### Automated test-suite setup
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as end-to-end tests.

All end-to-end tests must use the [Cypress](https://www.cypress.io/) E2E test framework.

All end-to-end test filenames must end with `.spec.js` or `.spec.ts`, and end-to-end test files with filenames that end with `.hidden.spec.js` or `.hidden.spec.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.js`, etc.

The `package.json` file may be updated to add any third-party libraries required for your assessment.

### Examples

Check out our `Vue` library assessments to see examples of how our Vue assesments are structured.
