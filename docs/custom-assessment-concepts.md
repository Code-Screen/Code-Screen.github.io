# Custom Assessment Concepts

CodeScreen is designed to give users full control over customizing their assessments. We provide template project setups for each supported language/framework, all using standard project structures for ease of use by developers familiar with the language or framework.

### Automated test-suite scoring
One of CodeScreen's key features is automated test-suite scoring. Test cases are implemented in code using testing libraries such as JUnit or XUnit, enabling a wide range of testing possibilities, such as object equality, integer comparison, proper exception handling, etc. This approach allows you to evaluate candidates in a manner consistent with real-world development practices.

When creating a custom assessment, you can specify the number of required passing unit/integration tests. This represents the minimum number of unit/integration tests a candidate's solution must pass for CodeScreen to <a href="https://docs.codescreen.com/#/viewing-candidates" target="_blank">mark</a> the candidate as having pass the assessment. You can also choose to include candidate-written unit/integration tests when calculating the total number of passing tests.

#### Immutability
You also have the option to mark exisiting unit/integration tests in an assessment as immutable or not. If they are immutable, CodeScreen will prevent candidates from altering unit test assertions to artificially pass tests, ensuring accurate candidate scores. The README for your assessment should clarify the immutability of unit tests and guide candidates on adding their own unit tests in separate files.

#### Hidden Tests
CodeScreen also supports a concept that we have named `Hidden Tests`. These are unit/integration tests that are not visible to the candidate but
are run against the candidate's solution when we process their code and generate the final report. Read [here](hidden-tests.md) for more details.

### Template repositories
Upon creating a custom assessment, a private `GitHub` template repository is generated for each selected language/framework. Each repo will contain a standard project structure in the given language/framework. 

When a candidate begins an assessment, a new private GitHub repository is created. This repo will just contain one commit (the initial commit) which contains the current contents of the `main` branch of your template repo. 

**Note** that candidates can't view commit history or other branches in your template repository, allowing you to iteratively improve the template repo over time with meaningful commit messages.

### Documentation
The documentation for creating custom assessments in all of our supported languages & frameworks are given below: <p>

  - **Frontend**
      - [Angular](creating-custom-angular-assessments.md)
      - [AngularJS](creating-custom-angular-js-assessments.md)
      - [React](creating-custom-react-assessments.md)
      - [Vue.js](creating-custom-vue-js-assessments.md)
      - [Svelte](creating-custom-svelte-assessments.md)
      - [Elm](creating-custom-elm-assessments.md)
      - [Web](creating-custom-web-assessments.md)

  - **Backend**
      - [Java (Maven)](creating-custom-java-maven-assessments.md)
      - [Java (Gradle)](creating-custom-java-gradle-assessments.md)
      - [Kotlin (Maven)](creating-custom-kotlin-maven-assessments.md)
      - [Kotlin (Gradle)](creating-custom-kotlin-gradle-assessments.md)
      - [Scala](creating-custom-scala-assessments.md)
      - [JavaScript (Node.js)](creating-custom-javascript-assessments.md)
      - [TypeScript (Node.js)](creating-custom-typescript-assessments.md)
      - [Python](creating-custom-python-assessments.md)
      - [Ruby](creating-custom-ruby-assessments.md)
      - [Go](creating-custom-go-assessments.md)
      - [PHP](creating-custom-php-assessments.md)
      - [.NET](creating-custom-csharp-assessments.md)
      - [C++](creating-custom-c-plus-plus-assessments.md)
      - [Rust](creating-custom-rust-assessments.md)
      - [Haskell](creating-custom-haskell-assessments.md)
      - [Elixir](creating-custom-elixir-assessments.md)

  - **Full-Stack**
      - [React + JavaScript (Node.js)](creating-custom-react-javascript-full-stack-assessments.md)
      - [React + Python](creating-custom-react-python-full-stack-assessments.md)
      - [React + .NET](creating-custom-react-csharp-full-stack-assessments.md)
      - [Other](creating-custom-full-stack-assessments.md)

  - **Mobile**
      - [React Native](creating-custom-react-native-assessments.md)
      - [Flutter](creating-custom-flutter-assessments.md)
      - [Swift](creating-custom-swift-assessments.md)

  - **DevOps**
      - [Terraform](creating-custom-terraform-assessments.md)
      - [Ansible](creating-custom-ansible-assessments.md)
      - [PowerShell](creating-custom-powershell-assessments.md)

  - **Web3/Blockchain**
      - [Solidity](creating-custom-solidity-assessments.md)

  - **Data Science**
      - [R](creating-custom-r-assessments.md)
    
  - **Other**
      - [WordPress](creating-custom-wordpress-assessments.md)
      - [Rails](creating-custom-rails-assessments.md)
