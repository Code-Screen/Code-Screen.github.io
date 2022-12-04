# Creating Custom Web Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Web</strong> from the drop-down list of available frontend frameworks, and set the time limit for the assessment.</br>

The <strong>Web</strong> option is suitable for when you want to create a custom frontend assessment that assessments a candidate's `HTML`, `CSS` and `JavaScipt/TypeScript` skills outside of a framework such as `React` or `Angular`.

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Web assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="webRepo.png" alt="Web Repo"/>
</figure>

</br></br>

You can then update this repository with details of your assessment and start sending the assessment to candidates.

### Automated test-suite setup
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit tests or end-to-end tests.

All unit tests files must use the [Jest](https://jestjs.io/) test framework, and all end-to-end tests must use the [Cypress](https://www.cypress.io/) E2E test framework.

All unit test filenames must end with `.test.js`, `.test.ts` or `.test.tsx`, and unit test files with filenames that end with `.hidden.test.js`,
 `.hidden.test.ts` or `.hidden.test.tsx` will not be visible to the candidate.

All end-to-end test filenames must end with `.spec.js` or `.spec.ts`, and end-to-end test files with filenames that end with `.hidden.spec.js` or `.hidden.spec.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.js`, etc.

The `package.json` file may be updated to add any third-party libraries and any `scripts` commands required for your assessment.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit & integration tests. We provide the following GitHub Action file for Web assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
name: Web CI

on: push

jobs:

  unit:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2

    - name: Install dependencies
      run: npm install

    - name: Run Jest tests
      run: npm test -- --passWithNoTests

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
        files: "cypress/integration/"

    - name: Install and run Cypress tests
      uses: cypress-io/github-action@v2
      if: steps.check_cypress_tests.outputs.files_exists == 'true'
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        build: npm run build --if-present
        start: npm start
        wait-on: 'http://localhost:3000'
```