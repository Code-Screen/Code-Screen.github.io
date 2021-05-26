# Custom Test Concepts

CodeScreen has been built from the ground up with the idea of users having complete control over customizing their assessments in mind.

<p>

CodeScreen provides template project setups for each of our supported languages & frameworks. These all use standard project structures, and as a result, will be very easy to use by developers familiar with that language/framework.

<p>

### Automated test-suite scoring
CodeScreen supports <strong>automated test-suite scoring</strong> in all of our supported backend languages.

CodeScreen test cases are implemented in code using testing libraries (such as <strong>JUnit</strong>, <strong>XUnit</strong>, etc.), which opens up an abundance of possibilities of what you can test for in a candidate's solution. </br> </br>Object equality, integer comparison (less than, greater than, etc.), proper exception handling, the sort order of lists, etc., are all now possible. </br></br>This allows you to test a candidate's solution in the same way your developers would test code in a real-world working environment.

<p>
  
**Note** that all unit test files you add are immutable, meaning that they cannot be edited by the candidate. This prevents the scenario whereby the candidate changes all the asserts in your unit tests to pass (e.g. `assert(true == true)`), resulting in CodeScreen marking those unit tests as passing tests and generating an inaccurate score for the candidate. The `README` for your test should include a note stating the unit tests are immutable and that if the candidate wants to add their own unit tests, they need to add these in a separate unit test file(s).
  
<p>

CodeScreen also supports a concept that we have named <strong>Hidden Tests</strong>. These are unit test cases that are not visible to the candidate but
are run against the candidate's solution when we process their code and generate the final report. Read [here](hiddenTests.md) for more details.

### Template repositories
Once you create a custom test, a private `GitHub` template repository will be created for each language/framework you chose for the test. These repos will contain standard project structures - see the individual language/framework guides below for more details.

**Note** that when a candidate begins a custom test that you send to them, a brand new private `GitHub` repo will be created. This repo will just contain one commit (the initial commit) which contains the current contents of the `master` branch of your template repo. 

The candidate will **not** be able to see the commit history or the other (non-master) branches in your template repo, which means you can keep on iterating on the template repo over time with meaningful commit messages, etc.

<p>

### Guides
The guides for creating custom assessments in all of our supported languages & frameworks are given below: <p>

  - [Java (Maven)](java.md)
  - [Java (Gradle)](java.gradle.md)
  - [Kotlin (Maven)](kotlin.maven.md)
  - [Kotlin (Gradle)](kotlin.gradle.md)
  - [Scala](scala.md)
  - [JavaScript](javascript.md)
  - [TypeScript](typescript.md)
  - [Python](python.md)
  - [Ruby](ruby.md)
  - [Go](go.md)
  - [PHP](php.md)
  - [.NET](csharp.md)
  - [C++](cpp.md)
  - [Solidity](solidity.md)
  - [Swift](swift.md)
  - [R](r.md)
  - [Angular](angular.md)
  - [AngularJS](angularjs.md)
  - [React](react.md)
  - [React Native](reactnative.md)
  - [Vue.js](vue.md)
  - [Rails](rails.md)
  - [Terraform](terraform.md)
  - [Ansible](ansible.md)
  - [PowerShell](powershell.md)
  - [Full-Stack](fullstack.md)



