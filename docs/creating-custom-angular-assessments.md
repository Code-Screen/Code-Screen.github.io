# Creating Custom Angular Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Angular</strong> from the drop-down list of available frontend frameworks, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Angular 13</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Angular assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="angularRepo.png" alt="Angular Repo"/>
</figure>

</br></br>

You can then update this repository with details of your Angular assessment and start sending the assessment to candidates.

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit tests or end-to-end tests.

All unit tests files must use the Angular default [Jasmine](https://angular.io/guide/testing) test framework & [Karma](https://angular.io/guide/testing) test runner and all end-to-end tests must use the [Cypress](https://www.cypress.io/) E2E test framework.

All unit test filenames must end with `.spec.ts` and unit test files with filenames that end with `.hidden.spec.ts` will not be visible to the candidate.

All end-to-end test filenames must end with `-spec.cy.ts`, and end-to-end test files with filenames that end with `-hidden-spec.cy.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden-foo.ts`, etc.

Your assessment must use `Angular 13`, and the `package.json` file may only be changed if you want to add third-party libraries to your assessment. All the current versions of the dependencies in `package.json` and `package-lock.json` must not be changed. 

The other config files in the template repo must also not be changed, including the `karma.conf.js` and `cypress.config.ts` files.

### Examples

Please see our Angular library assessments for more information on how our Angular automated test suites are set up.
