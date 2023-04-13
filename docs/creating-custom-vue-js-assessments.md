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
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as either unit tests or end-to-end tests.

All unit tests must use [Vitest](https://vitest.dev/) test framework and all end-to-end tests must use the [Cypress](https://www.cypress.io/) E2E test framework.

All unit test filenames must end with `.test.js` or `.test.ts`, and end-to-end test files with filenames that end with `.hidden.test.js` or `.hidden.test.ts` will not be visible to the candidate.

All end-to-end test filenames must end with `.spec.js` or `.spec.ts`, and end-to-end test files with filenames that end with `.hidden.spec.js` or `.hidden.spec.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.js`, etc.

The `package.json` file may be updated to add any third-party libraries required for your assessment.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated integration tests. We provide the following GitHub Action file for Vue assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
name: Vue CI

on: push

jobs:

  unit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Install dependencies
        run: npm install

      - name: Run Vitest tests
        run: npm run test:unit -- --passWithNoTests

  e2e:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2

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
          start: npm run dev -- --host
          wait-on: 'http://localhost:5173'
```

### Examples

Check out our `Vue` library assessments to see examples of how our Vue assesments are structured.
