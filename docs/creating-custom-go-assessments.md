# Creating Custom Go Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Go</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Go</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Go assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="goRepo.png" alt="Go Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add assessments that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as assessment files.

All unit test filenames must end with `_assessment.go` and all unit test files with names ending with `_hidden_assessment.go` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.go` etc.

All unit tests must use the [`Ginkgo`](http://onsi.github.io/ginkgo/) assessment framework.

The coding assessment must be compatible with `Go 1.19`.

All dependencies that your coding assessment requires need to be added to the `go.mod` file.

### Examples

An **example** `Go` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Go-CodeScreen-Fibonacci
