# Creating Custom Java (Gradle) Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Java (Gradle)</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Gradle</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Java (Gradle) assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="java_gradle_repo.png" alt="Java Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `src/test/java/` directory.

All unit test filenames must end with `"Test"` and all unit test filesnames that end with `"HiddenTest"` will not be visible to the candidate. These hidden tests allow you to test candidate's solutions against edge cases etc.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.java`, etc.

All unit tests must use the [`Junit`](https://junit.org/junit5/) test framework and the `build.gradle` file may only be updated to add dependencies required for your coding test.

The coding test must be compatible with `Java 16`.

### Examples

An **example** `Java (Gradle)` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Java-Gradle-CodeScreen-Fibonacci