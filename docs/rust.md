# Creating Custom Rust Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Rust</strong> from the drop-down list of available backend languages, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Rust</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Rust assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="rustRepo.png" alt="Rust Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files in the `tests/` directory.

All tests files must be added in the `tests/` directory and use the `assert Macros` from the `Rust standard library`.

All test filenames must end with `_test.rs` and test files with filenames that end with `_hidden_test.rs` will not be visible to the candidate.

The `Cargo.toml` file should only be modified in order to add any third-party dependencies required for your solution.

The `Cargo 2018` edition must be used.

The maximum memory allowed for a solution to your coding test is 4G.

### Examples

An **example** `Rust` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Rust-CodeScreen-Fibonacci
