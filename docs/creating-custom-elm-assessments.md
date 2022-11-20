# Creating Custom Elm Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Elm</strong> from the drop-down list of available Frontend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access. This repository will contain a skeleton <strong>Elm</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Elm assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="elmRepo.png" alt="Elm Repo"/>
</figure>

</br>

### Automated test-suite setup

If you would like to add unit tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All test files with filenames that end with `Hidden.elm` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.hs`, etc.

The `elm.json` file should only be modified in order to add any third-party dependencies required for your assessment.

Your coding assessment must use/be comptabible with Elm version `0.19.1`.

### Examples

An **example** `Elm` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Elm-CodeScreen-Example
