# Creating Custom Rust Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.</br>

You can then add the description of your assessment, choose <strong>Rust</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Rust</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Rust assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="rustRepo.png" alt="Rust Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All unit test files must be added in the `tests/` directory and use the `assert Macros` from the `Rust standard library`.

All test filenames must end with `_test.rs` and test files with filenames that end with `_hidden_test.rs` will not be visible to the candidate.

If you want to add files that your hidden tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.rs`, etc.

The `Cargo.toml` file should only be modified in order to add any third-party dependencies required for your solution.

The `Cargo 2018` edition must be used.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Rust assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Rust CI

on: [push]

jobs:
  build_and_test:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - uses: actions-rs/toolchain@v1
      with:
        toolchain: stable

    - name: Build
      uses: actions-rs/cargo@v1
      with:
        command: build
        args: --release --all-features

    - name: Test
      run: cargo test --no-fail-fast
```


### Examples

An **example** `Rust` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Rust-CodeScreen-Fibonacci
