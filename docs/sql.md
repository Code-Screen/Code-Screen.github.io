# Creating Custom SQL Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>SQL</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a `Node.js` project with a sample `SQLite` database, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom SQL assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="sqlRepo.png" alt="SQL Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `tests/` directory.

All unit tests use the `Jest` testing framework.

All unit test file names must end with `.spec.js` and all unit test files with file names ending with `.hidden.spec.js` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden-foo.js`, etc.

The `package.json` file should only be modified in order to add any third-party dependencies required for your solution. The `jest`, `babel` and `sqlite3` versions should not be changed.

The coding test must be compatible with Node.js version `15.5.1`.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

Check out the template repo or any of our `SQL` library assessments to see examples of how our SQL assesments are structured.
