# Creating Custom JavaScript (Node.js) Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>JavaScript</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Node.js</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom JavaScript (Node.js) assessment GitHub repository:</figcaption>
  </br>
  <img src="javascriptRepo.png" alt="JavaScript Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `tests/` directory.

All unit tests must be added in the `tests/` directory and use the [`Mocha`](https://mochajs.org) testing framework alongside the [`Chai`](https://www.chaijs.com) assertion library.

All unit test file names must end with `.test.js` and all unit test files with file names ending with `.hidden.test.js` will not be visible to the candidate.

All dependencies required for your coding test must be added to the `package.json` file.

The coding test must be compatible with Node.js version 11.7.0.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `JavaScript` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/JavaScript-CodeScreen-Fibonacci
