# Creating Custom Solidity Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Solidity</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Solidity</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Solidity assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="solidityRepo.png" alt="Solidity Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files in the `test/` directory.

All unit tests must use the `Truffle` testing framework. They can be written in either `Solidity` or `JavaScript`.

All unit test file names must end with `Test.js` or `Test.sol`, and all unit test files with file names ending with `HiddenTest.js` or `HiddenTest.sol` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of 
these files must begin with `hidden` (case-insensitive), e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `HiddenFoo.sol`, etc.

The `package.json` file should only be modified in order to add any third-party dependencies required for your solution. The `truffle` and `truffle-assertions` versions should not be changed.

The `pragma` version also must not be changed.

The coding assessment must be compatible with Node.js version `15.5.1`.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Solidity assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
name: Solidity CI

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [15.x]

    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v3
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        node-version: ${{ matrix.node-version }}
    - run: npm ci
    - run: npm test
```

### Examples

An **example** `Solidity` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Solidity-CodeScreen-Fibonacci
