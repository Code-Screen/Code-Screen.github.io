# Creating Custom Vue.js Assessments
To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Frontend</strong> category and then choose `Vue.js` from the drop-down list of available frontend frameworks.

Once you create an assessment, a private GitHub repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton Vue project, and the `README.md` will contain the description of the assessment that you added during the setup.

<br>

<figure>
  <figcaption style="font-style: italic;">Example custom Vue assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="vue.png" alt="Vue.js Repo"/>
</figure>

</br></br>

You can then update this repository with details of your Vue assessment and start sending the assessment to candidates.

### Automated test-suite setup
If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as either unit tests or end-to-end tests.

All unit tests must use `Vitest` test framework and all end-to-end tests must use the `Cypress` E2E test framework.

The `package.json` file may be updated to add any third-party libraries required for your assessment.

#### Naming Conventions

- Unit test filenames must end with `.test.js` or `.test.ts`. Files with names ending in `.hidden.test.js`, or `.hidden.test.ts` will be hidden from the candidate.
- End-to-end test filenames must end with `.spec.js` or `.spec.ts`. Files with names ending in `.hidden.spec.js` or `.hidden.spec.ts` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.js`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated integration tests. We provide the following GitHub Action file for Vue assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Vue CI

on: push

jobs:

  unit:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Install dependencies
        run: npm install

      - name: Run Vitest tests
        run: npm run test:unit -- --passWithNoTests

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
