# Creating Custom Swift Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Swift</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton `Xcode` project, and the README will contain the description of the assessment that you added during the setup.</br></br>

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

All unit test class filenames must end with `Tests.swift` and the test classes with filenames that end with `HiddenTests.swift` will not be visible to the candidate. All unit tests must use the [XCTest](https://developer.apple.com/documentation/xctest) testing framework.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.swift`, etc.

`Xcode` version 14 must be used.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Swift assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
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
