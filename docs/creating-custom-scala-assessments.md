# Creating Custom Scala Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Scala</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>SBT</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Scala assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="scalaRepo.png" alt="Scala Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `src/test/` directory.

All unit tests files must end with `Test.scala` and all unit tests files that end with `HiddenTest.scala` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.scala`, etc.

All unit tests must use the [`JUnit`](https://junit.org/junit5/) assessment framework.

The name of the project in the `build.sbt` should be updated to better match your assessment, and any dependencies required for your coding assessment must be added to the `build.sbt` file.

The `Scala` version that must be used is 2.13.6.

### Examples

An **example** `Scala` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Scala-CodeScreen-Fibonacci
