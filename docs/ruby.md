# Creating Custom Ruby Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Ruby</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Ruby</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Ruby assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="rubyRepo.png" alt="Ruby Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files in the `tests/` directory.

All unit tests files must be added in the `tests/` directory and use the [`Test::Unit`](https://test-unit.github.io/) testing framework.

All unit test filenames must begin with `test_` and unit test files with filenames that begin with `test_hidden` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, etc.

All dependencies required for your coding test must be added to the `Gemfile`.

Your coding test also must use/be compatible with `Ruby version 3.0`.

The current content of the `Rakefile` must not be modified. You may add to the `Rakefile` as required for your coding test.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `Ruby` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Ruby-CodeScreen-Fibonacci
