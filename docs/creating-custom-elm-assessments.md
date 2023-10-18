# Creating Custom Elm Assessments
To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Frontend</strong> category and then choose `Elm` from the drop-down list of available frontend frameworks.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access. 

This repository will contain a skeleton Elm project, and the `README.md` file will contain the description of the assessment that you added during the setup.

</br>

<figure>
  <figcaption style="font-style: italic;">Example custom Elm assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="elmRepo.png" alt="Elm Repo"/>
</figure>

</br>

### Automated test-suite setup

If you would like to add unit tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All test files with filenames that end with `Hidden.elm` will not be visible to the candidate.

The `elm.json` file should only be modified in order to add any third-party dependencies required for your assessment.

Your coding assessment must use/be comptabible with Elm version `0.19.1`.

#### Naming Conventions

- Unit test filenames ending in `Hidden.elm` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Elm assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Elm CI

on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - uses: jorelali/setup-elm@v3
      with:
        elm-version: 0.19.1
    - run: npx elm-test
```

### Examples

An **example** `Elm` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Elm-CodeScreen-Example
