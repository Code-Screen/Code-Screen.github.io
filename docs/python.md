# Creating Custom Python Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Python</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Python</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Python assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 60%;" src="pythonRepo.png" alt="Python Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files in the `tests/` directory.

All unit test filenames must begin with `test_` and all test files with names beginning with `test_hidden_` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, etc.

All unit tests must use the [`pytest`](https://docs.pytest.org/en/latest/) unit test framework, version `6.0.0`.

Any dependencies required for your coding test need to be included in the `requirements.txt` file and must be available to download using the 
[`pip`](https://pip.pypa.io/en/stable/) package installer.

The Python code must be compatible with `Python` version `3.8`.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `Python` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Python-CodeScreen-Fibonacci
