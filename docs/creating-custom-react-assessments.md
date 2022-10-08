# Creating Custom React Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>React</strong> from the drop-down list of available frontend frameworks, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>React</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom React assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="reactRepo.png" alt="React Repo"/>
</figure>

</br></br>

You can then update this repository with details of your React assessment and start sending the assessment to candidates.

### Automated test-suite setup
If you would like to add assessments that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit tests or end-to-end assessments.

All unit tests files must use the [Jest](https://jestjs.io/) assessment framework, and all end-to-end assessments must use the [Cypress](https://www.cypress.io/) E2E assessment framework.

All unit test filenames must end with `.assessment.js`, `.assessment.ts` or `.assessment.tsx`, and unit test files with filenames that end with `.hidden.assessment.js`,
 `.hidden.assessment.ts` or `.hidden.assessment.tsx` will not be visible to the candidate.

All end-to-end assessment filenames must end with `.spec.js` or `.spec.ts`, and end-to-end assessment files with filenames that end with `.hidden.spec.js` or `.hidden.spec.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.js`, etc.

The `package.json` file may be updated to add any third-party libraries required for your assessment.

### Examples

An **example** `React` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/React-CodeScreen-Stadiums-Example