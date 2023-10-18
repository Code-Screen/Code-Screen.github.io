# Creating Custom Solidity Assessments

To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.

You can then add the description of your assessment, select the <strong>Web3/Blockchain</strong> category and then choose `Solidity` from the drop-down list of available languages.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

This repository will contain a skeleton Solidity project, and the `README.md` file will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Solidity assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="solidityRepo.png" alt="Solidity Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files in the `test/` directory.

All unit tests must use the `Truffle` testing framework. They can be written in either `Solidity` or `JavaScript`.

The `package.json` file should only be modified in order to add any third-party dependencies required for your solution. The `truffle` and `truffle-assertions` versions should not be changed.

The `pragma` version also must not be changed.

The coding assessment must be compatible with Node.js version `18.x`.

#### Naming Conventions

- Unit test filenames must end with `Test.js` or `Test.sol`. Files with names ending in `HiddenTest.js` or `HiddenTest.sol` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.js`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Solidity assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Solidity CI

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [18.x]

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
