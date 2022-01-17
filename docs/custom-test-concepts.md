# Custom Test Concepts

CodeScreen has been built from the ground up with the idea of users having complete control over customizing their assessments in mind.

<p>

CodeScreen provides template project setups for each of our supported languages & frameworks. These all use standard project structures, and as a result, will be very easy to use by developers familiar with that language/framework.

<p>

### Automated test-suite scoring
CodeScreen supports <strong>automated test-suite scoring</strong> in all of our supported backend languages.

CodeScreen test cases are implemented in code using testing libraries (such as <strong>JUnit</strong>, <strong>XUnit</strong>, etc.), which opens up an abundance of possibilities of what you can test for in a candidate's solution. </br> </br>Object equality, integer comparison (less than, greater than, etc.), proper exception handling, the sort order of lists, etc., are all now possible. </br></br>This allows you to test a candidate's solution in the same way your developers would test code in a real-world working environment.

When creating a new custom test, you can set the number of **required passing unit tests**. This is the minimum number of unit tests a candidate's solution must pass for us to mark the candidate as having passed the test. We also provide the option to include the passing unit tests that were written by the candidate when checking did the total number of passing unit tests equal or exceed  the require passing unit tests number.

<p>
  
**Note** that all unit test files you add are **immutable**, meaning that they cannot be edited by the candidate. <br> This prevents the scenario whereby the candidate changes all the asserts in your unit tests to pass (e.g. `assert(true == true)`), resulting in CodeScreen marking those unit tests as passing tests and generating an inaccurate score for the candidate. <br> The `README` for your test should include a note stating the unit tests are immutable and that if the candidate wants to add their own unit tests, they need to add these in a separate unit test file(s).
  
<p>

CodeScreen also supports a concept that we have named <strong>Hidden Tests</strong>. These are unit test cases that are not visible to the candidate but
are run against the candidate's solution when we process their code and generate the final report. Read [here](hidden-tests.md) for more details.

### Template repositories
Once you create a custom test, a private `GitHub` template repository will be created for each language/framework you chose for the test. These repos will contain standard project structures - see the individual language/framework guides below for more details.

**Note** that when a candidate begins a custom test that you send to them, a brand new private `GitHub` repo will be created. This repo will just contain one commit (the initial commit) which contains the current contents of the `main` branch of your template repo. 

The candidate will **not** be able to see the commit history or the other (non-main) branches in your template repo, which means you can keep on iterating on the template repo over time with meaningful commit messages, etc.

<p>

### Guides
The guides for creating custom assessments in all of our supported languages & frameworks are given below: <p>

  - [Java (Maven)](creating-custom-java-maven-assessments.md)
  - [Java (Gradle)](creating-custom-java-gradle-assessments.md)
  - [Kotlin (Maven)](creating-custom-kotlin-maven-assessments.md)
  - [Kotlin (Gradle)](creating-custom-kotlin-gradle-assessments.md)
  - [Scala](creating-custom-scala-assessments.md)
  - [JavaScript](creating-custom-javascript-assessments.md)
  - [TypeScript](creating-custom-typescript-assessments.md)
  - [Python](creating-custom-python-assessments.md)
  - [Ruby](creating-custom-ruby-assessments.md)
  - [Go](creating-custom-go-assessments.md)
  - [PHP](creating-custom-php-assessments.md)
  - [.NET](creating-custom-csharp-assessments.md)
  - [C++](creating-custom-c-plus-plus-assessments.md)
  - [Rust](creating-custom-rust-assessments.md)
  - [Haskell](creating-custom-haskell-assessments.md)
  - [Elixir](creating-custom-elixir-assessments.md)
  - [Solidity](creating-custom-solidity-assessments.md)
  - [Swift](creating-custom-swift-assessments.md)
  - [R](creating-custom-r-assessments.md)
  - [Web](creating-custom-web-assessments.md)
  - [Angular](creating-custom-angular-assessments.md)
  - [AngularJS](creating-custom-angular-js-assessments.md)
  - [React](creating-custom-react-assessments.md)
  - [React Native](creating-custom-react-native-assessments.md)
  - [Vue.js](creating-custom-vue-js-assessments.md)
  - [Rails](creating-custom-rails-assessments.md)
  - [Django](creating-custom-django-assessments.md)
  - [WordPress](creating-custom-wordpress-assessments.md)
  - [Terraform](creating-custom-terraform-assessments.md)
  - [Ansible](creating-custom-ansible-assessments.md)
  - [PowerShell](creating-custom-powershell-assessments.md)
  - [Full-Stack](creating-custom-full-stack-assessments.md)
