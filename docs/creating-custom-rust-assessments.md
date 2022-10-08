# Creating Custom Rust Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/#/login), click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.</br>

You can then add the description of your assessment, choose <strong>Rust</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Rust</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Rust assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="rustRepo.png" alt="Rust Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add assessments that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as assessment files in the `tests/` directory.

All assessments files must be added in the `assessments/` directory and use the `assert Macros` from the `Rust standard library`.

All assessment filenames must end with `_assessment.rs` and assessment files with filenames that end with `_hidden_assessment.rs` will not be visible to the candidate.

If you want to add files that your hidden unit tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.rs`, etc.

The `Cargo.toml` file should only be modified in order to add any third-party dependencies required for your solution.

The `Cargo 2018` edition must be used.

### Examples

An **example** `Rust` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Rust-CodeScreen-Fibonacci
