# Creating Custom React Native Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>React Native</strong> from the drop-down list of available frontend frameworks, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>React Native</strong> project created with [Expo](https://expo.dev/), and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom React Native assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="reactNativeRepo.png" alt="React Native Repo"/>
</figure>

</br></br>

You can then update this repository with details of your assessment and start sending the assessment to candidates.

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as end-to-end tests.

All end-to-end tests must use the [Cypress](https://www.cypress.io/) E2E test framework.

All end-to-end test filenames must end with `.cy.js`, and end-to-end test files with filenames that end with `-hidden.cy.js` will not be visible to the candidate.

If you want to add files that your hidden end to end assessments use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden-foo.ts`, etc.

The `package.json` file may only be changed if you want to add third-party libraries to your assessment. All the current versions of the dependencies in `package.json` and `package-lock.json` must not be changed. 

The other config files in the template repo must also not be changed, including the `babel.config.js` and `cypress.config.js` files.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated integration tests. We provide the following GitHub Action file for React Native assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
name: React Native CI

on: push

jobs:

  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Install dependencies
        run: npm install

      - name: Install Expo CLI
        run: npm i -g expo-cli

      - name: Check Cypress tests exist
        id: check_cypress_tests
        uses: andstor/file-existence-action@v1
        with:
          files: "cypress/e2e/"

      - name: Install and run Cypress tests
        uses: cypress-io/github-action@v4
        if: steps.check_cypress_tests.outputs.files_exists == 'true'
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          build: npm run build --if-present
          start: npm run web
          wait-on: 'http://localhost:19006'
```

### Examples

Please see our React Native library assessments for more information on how our React Native automated test suites are set up.
