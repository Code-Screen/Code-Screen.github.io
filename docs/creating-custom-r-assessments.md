# Creating Custom R Assessments

To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Data Science</strong> category and then choose `R` from the drop-down list of available languages.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton R project, and the `README.md` will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom R assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="rRepo.png" alt="R Repo"/>
</figure>

</br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All dependencies required for your coding assessment must be added to the `install.sh` file.

The `install.R` and `run_tests.sh` files should not be modified.

Your coding assessment also must use/be compatible with `R` version `4.0.3`.

All unit tests files must be added in the `tests/` directory and use the [testthat](https://testthat.r-lib.org/) package.

#### Naming Conventions

- Unit test filenames must begin with `test_`. Files with names beginning in `test_hidden` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `hidden_foo.R`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for R assessments.

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: R CI

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - name: Set up environment
      uses: r-lib/actions/setup-r@v2
      with:
        r-version: '4.0.3'

    - name: Download dependencies
      run: ./install.sh

    - name: Run tests
      run: ./run_tests.sh
```

### Examples

An **example** `R` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/R-CodeScreen-Increment-Func
