# Creating Custom Ruby Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.com/account/login), click <strong>Add new assessment</strong>, and click the <strong>Custom</strong> button.</br>

You can then add the description of your assessment, choose <strong>Ruby</strong> from the drop-down list of available backend languages, and set the time limit for the assessment.</br>

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Ruby</strong> project, and the README will contain the description of the assessment that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Ruby assessment GitHub repository:</figcaption>
  </br>
  <img style="max-width: 70%;" src="rubyRepo.png" alt="Ruby Repo"/>
</figure>

</br></br>

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit test files in the `tests/` directory.

All unit tests files must be added in the `tests/` directory and use the [`Test::Unit`](https://test-unit.github.io/) testing framework.

All unit test filenames must begin with `test_` and unit test files with filenames that begin with `test_hidden` will not be visible to the candidate.

If you want to add files that your hidden tests use and hence are also not visible to the candidate, the names of these files must begin with `hidden`, e.g., `hiddenFoo.json`, `hiddenFoo.csv`, `hidden_foo.rb`, etc.

If you want entire folders to be hidden, the folder needs to be in the root of the repo and the folder name needs to start with `hidden`, e.g. `/hidden-files`.

All dependencies required for your coding assessment must be added to the `Gemfile`.

Your coding assessment also must use/be compatible with `Ruby version 3.0`.

The current content of the `Rakefile` must not be modified. You may add to the `Rakefile` as required for your coding assessment.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit tests. We provide the following GitHub Action file for Ruby assessments. **Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: Ruby

on: [push]

jobs:
  test:

    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
    - name: Set up Ruby
      uses: ruby/setup-ruby@473e4d8fe5dd94ee328fdfca9f8c9c7afc9dae5e
      with:
        ruby-version: 3.0
    - name: Install
      run: bundle install
    - name: Test
      run: bundle exec rake test
```

### Examples

An **example** `Ruby` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Ruby-CodeScreen-Fibonacci
