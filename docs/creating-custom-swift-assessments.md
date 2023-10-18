# Creating Custom Swift Assessments

To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Mobile</strong> category and then choose `Swift` from the drop-down list of available languages.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton `Xcode` project, and the `README.md` will contain the description of the assessment that you added during the setup.</br>

<figure>
  <figcaption style="font-style: italic;">Example custom Swift assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="swiftRepo1.png" alt="Swift Repo 1"/>
</figure>

<figure>
  <figcaption style="font-style: italic;">Example custom Swift assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="swiftRepo2.png" alt="Swift Repo 2"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test classes in the `iOS-CodeScreen/iOS-CodeScreenTests/` directory.

All unit tests must use the [XCTest](https://developer.apple.com/documentation/xctest) testing framework.

`Xcode` version 14 must be used.

#### Naming Conventions

- Unit test filenames must start with `Tests.swift`. Files with names starting in `HiddenTests.swift` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.swift`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Swift assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Swift CI

on: push

jobs:
  build:
    runs-on: macos-12

    steps:
      - uses: actions/checkout@v3
      - uses: maxim-lobanov/setup-xcode@v1
        with:
          xcode-version: '14'

      - name: Build App
        run: cd iOS-CodeScreen; xcodebuild -scheme iOS-CodeScreen -destination "platform=iOS Simulator,name=iPhone 14,OS=latest"

      - name: Run tests
        run: cd iOS-CodeScreen; xcodebuild clean -scheme iOS-CodeScreen test -destination "platform=iOS Simulator,name=iPhone 14,OS=latest"
```

### Examples

Check out our `Swift` library assessments to see examples of how our Swift assesments are structured.
