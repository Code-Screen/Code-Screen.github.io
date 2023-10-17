# Creating Custom Elm Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Elm</strong> from the drop-down list of available Frontend languages, and set the time limit for the assessment.</br>

Once you create an assessment, a private GitHub repository will be created in the CodeScreen account, and you will be given access. This repository will contain a skeleton <strong>Elm</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Elm assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="elmRepo.png" alt="Elm Repo"/>
</figure>

</br>

### Automated test-suite setup

If you would like to add unit tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All test files with filenames that end with `Hidden.elm` will not be visible to the candidate.

If you want to add files that your hidden tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.hs`, etc.

The `elm.json` file should only be modified in order to add any third-party dependencies required for your assessment.

Your coding assessment must use/be comptabible with Elm version `0.19.1`.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Elm assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

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
