# Creating Custom Python Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Python</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Python</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Python assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="pythonRepo.png" alt="Python Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add assessments that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as assessment files in the `tests/` directory.

All unit test filenames must begin with `test_` and all unit test files with names beginning with `test_hidden_` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.py`, etc.

All unit tests must use the [`pyassessment`](https://docs.pyassessment.org/en/laassessment/) unit test framework, version `6.0.0`.

Any dependencies required for your coding assessment need to be included in the `requirements.txt` file and must be available to download using the 
[`pip`](https://pip.pypa.io/en/stable/) package installer.

The Python code must be compatible with `Python` version `3.8`.

### Examples

An **example** `Python` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Python-CodeScreen-Fibonacci
