# Creating Custom Angular Assessments
CodeScreen allows you to add your own assessment and send it to candidates.</br></br>
To begin, log on to [CodeScreen](https://app.codescreen.dev/#/login), click <strong>Add new test</strong>, and select <strong>Custom test</strong>.</br>

You can then add the description of your test, choose <strong>Angular</strong> from the drop-down list of available frontend frameworks, and set the time limit for the test.</br>

Once you click <strong>Publish</strong>, a private GitHub repository will be created in the CodeScreen account, and you will be given access.
This repository will contain a skeleton <strong>Angular 8</strong> project, and the README will contain the description of the test that you added during the setup.</br></br>

<figure>
  <figcaption style="font-style: italic;">Example custom Angular assessment GitHub repository:</figcaption>
  </br>
  <img src="angularRepo.png" alt="Angular Repo"/>
</figure>

</br></br>

You can then update this repository with details of your Angular assessment and start sending the test to candidates.

### Automated test-suite setup

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as test files that end with `.spec.ts`.

All unit tests files must use the Angular default [`Jasmine`](https://angular.io/guide/testing) test framework and [`Karma`](https://angular.io/guide/testing)
test runner.

All unit test filenames must end with `.spec.ts` and unit test files with filenames that end with `.hidden.spec.ts` will not be visible to the candidate.

Your test must use `Angular 8`, and the `package.json` file may only be changed if you want to add third-party libraries to your test. All the current versions of the dependencies in `package.json` and `package-lock.json` must not be changed. 

The root `tsconfig.json` file, the application-source files (`pollyfills.ts`, `main.ts`, `test.ts`), and the application-specific config files (`karma.conf.js`, `tsconfig.app.json`, `tsconfig.spec.json`) must also not be modified.

### Examples

An **example** `Angular` assessment that uses automated test suite scoring can be seen here:<br/>
https://github.com/Code-Screen/Angular-CodeScreen-Stadiums-Example