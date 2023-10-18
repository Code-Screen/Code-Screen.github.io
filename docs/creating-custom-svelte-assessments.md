# Creating Custom Svelte Assessments

To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Frontend</strong> category and then choose `Svelte` from the drop-down list of available frontend frameworks.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton Svelte project, and the `README.md` will contain the description of the assessment that you added during the setup.

</br>

<figure>
  <figcaption style="font-style: italic;">Example custom Svelte assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="svelte.png" alt="Svelte Repo"/>
</figure>

</br></br>

You can then update this repository with details of your Svelte assessment and start sending the assessment to candidates.

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as end-to-end tests.

All end-to-end tests must use the `Cypress` E2E test framework.

The `package.json` file may be updated to add any third-party libraries required for your assessment.

#### Naming Conventions

- End-to-end test filenames must end with `.spec.ts`. Files with names ending in `hidden.spec.ts` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.js`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated integration tests. We provide the following GitHub Action file for Svelte assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Svelte CI

on: push

jobs:

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
          start: npm run dev -- --open --host
          wait-on: 'http://localhost:5173'
```
