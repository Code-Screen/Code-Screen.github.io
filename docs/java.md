# Creating Custom Java Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Java</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Maven</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Java assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="java_repo.png" alt="Java Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `src/test/java/` directory.

All unit test class names must end with `"Test"` and all unit test classes with names that end with `"HiddenTest"` will not be visible to the candidate. These hidden tests allow you to test candidate's solutions against edge cases etc.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, etc.

All unit tests must use the [`Junit`](https://junit.org/junit5/) test framework and the `pom.xml` file may only be updated to add dependencies required for your coding test.

The coding test must be compatible with `Java 11`.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `Java` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Java-CodeScreen-Fibonacci
