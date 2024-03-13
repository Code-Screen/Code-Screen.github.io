# Creating Custom React Native Assessments
To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Mobile</strong> category and then choose `React Native` from the drop-down list of available languages.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton React Native project created with [Expo](https://expo.dev/), and the `README.md` will contain the description of the assessment that you added during the setup.</br>

<figure>
  <figcaption style="font-style: italic;">Example custom React Native assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="reactNativeRepo.png" alt="React Native Repo"/>
</figure>

</br></br>

You can then update this repository with details of your assessment and start sending the assessment to candidates.

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as end-to-end tests.

All end-to-end tests must use the `Cypress` E2E test framework.

The `package.json` file may only be changed if you want to add third-party libraries to your assessment. All the current versions of the dependencies in `package.json` must not be changed. 

The other config files in the template repo must also not be changed, including the `babel.config.js` and `cypress.config.js` files.

#### Naming Conventions

- End-to-end test filenames must end with `.cy.js`. Files with names ending in `-hidden.cy.js` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.js`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated integration tests. We provide the following GitHub Action file for React Native assessments.

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: React Native CI

on: push

jobs:

  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install dependencies
        run: npm install

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
          wait-on: 'http://localhost:8081'
```

### Examples

Please see our React Native library assessments for more information on how our React Native automated test suites are set up.
