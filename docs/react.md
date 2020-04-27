# Creating Custom React Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>React</strong> from the drop-down list of available frontend frameworks, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>React</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom React assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="reactRepo.png" alt="React Repo"/>
</figure>

</br></br>

You can then update this repository with details of your React assessment and start sending the test to candidates.

### Automated test-suite setup
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files that end with `.test.js`.

All unit tests files must use the [`Jest`](https://jestjs.io/) test framework, and all end-to-end tests must use the [`Cypress`](https://www.cypress.io/) E2E test framework.

All unit test filenames must end with `.test.js` and unit test files with filenames that end with `.hidden.test.js` will not be visible to the candidate.
All end-to-end test filenames must end with `.spec.js` and end-to-end test files with filenames that end with `.hidden.spec.js` will not be visible to the candidate.

The `package.json` file may be updated to add any third-party libraries required for your test.

### Examples

An **example** `React` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/React-CodeScreen-Stadiums-Example