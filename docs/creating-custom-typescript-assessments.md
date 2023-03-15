# Creating Custom TypeScript (Node.js) Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>TypeScript</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton `TypeScript Node.js` project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom TypeScript (Node.js) assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="typescriptRepo.png" alt="TypeScript Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All unit tests use the `Jest` testing framework.

All unit test file names must end with `.spec.ts` and all unit test files with file names ending with `.hidden.spec.ts` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden-foo.ts`, etc.

The `package.json` file should only be modified in order to add any third-party dependencies required for your solution. The `jest` and `babel` versions should not be changed.

The coding assessment must be compatible with Node.js version `18`.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for TypeScript (Node.js) assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```
name: Node.js CI

on: push

jobs:
  build:

    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [18.x]

    steps:
    - uses: actions/checkout@v2
    - name: Use Node.js ${{ matrix.node-version }}
      uses: actions/setup-node@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        node-version: ${{ matrix.node-version }}
    - run: npm install
    - run: npm ci
    - run: npm run build --if-present
    - run: npm test -- --passWithNoTests
```

### Examples

An **example** `TypeScript` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/TypeScript-CodeScreen-Fibonacci
