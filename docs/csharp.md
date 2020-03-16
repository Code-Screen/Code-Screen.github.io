# Creating Custom .NET Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>.NET</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>.NET</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom .NET assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="csharpRepo.png" alt=".NET Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `test/` directory.

All unit test class names must end with `"Test"` and all unit test classes with names that end with `"HiddenTest"` will not be visible to the candidate.

All unit tests must use the [`Nunit`](https://nunit.org/) test framework.

The `.csproj` file should be renamed, and the `RootNamespace` element in this file must be updated to match this
new name. The only other updates that should go in to the `.csproj` file are dependencies required for your coding test.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `.NET` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Csharp-CodeScreen-Fibonacci
