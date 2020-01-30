# Creating Custom Go Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Go</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Go</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Go assessment GitHub repository:</figcaption>
  </br>
  <img src="goRepo.png" alt="Go Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files.

All unit test filenames must end with `_test.go` and all unit test files with names ending with `_hidden_test.go` will not be visible to the candidate.

All unit tests must use the [`Ginkgo`](http://onsi.github.io/ginkgo/) test framework.

All dependencies that your coding test requires need to be added to the `go.mod` file.

The maximum memory allowed for a solution to your coding test is 4G.

The Go code must be compatible with `Go` version 1.7.

### Examples

An **example** `Go` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Go-CodeScreen-Fibonacci
