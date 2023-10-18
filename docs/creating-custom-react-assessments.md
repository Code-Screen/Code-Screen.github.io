# Creating Custom React Assessments
To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Frontend</strong> category and then choose `React` from the drop-down list of available frontend frameworks.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton React project, and the `README.md` will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom React assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="reactRepo.png" alt="React Repo"/>
</figure>

</br></br>

You can then update this repository with details of your React assessment and start sending the assessment to candidates.

### Automated test-suite setup
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit tests or end-to-end tests.

All unit tests files must use the `Jest` `Vitest` test framework, and all end-to-end tests must use the `Cypress` E2E test framework.

You can use either `Create React App` or `Vite` as your project build tool.

#### Naming Conventions

- Unit test filenames must end with `.test.js`, `.test.jsx`, `.test.ts`, or `.test.tsx`. Files with names ending in `.hidden.test.js`, `.hidden.test.jsx`, `.hidden.test.ts`, or `.hidden.test.tsx` will be hidden from the candidate.
- End-to-end test filenames must end with `.cy.js` or `.cy.ts`. Files with names ending in `.hidden.cy.js` or `.hidden.cy.ts` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.js`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit & integration tests. We provide the following GitHub Action file for React assessments.

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: React CI

on: push

jobs:

  unit:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v3

    - name: Install dependencies
      run: npm install

    - name: Run unit tests
      run: npm test -- --passWithNoTests
      env:
        CI: false

  e2e:
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
      uses: cypress-io/github-action@v5
      if: steps.check_cypress_tests.outputs.files_exists == 'true'
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        build: npm run build --if-present
        start: npm start
        wait-on: 'http://localhost:3000'
```

### Examples

Check out our `React` library assessments to see examples of how our React assesments are structured.