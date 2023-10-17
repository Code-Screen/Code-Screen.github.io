# Creating Custom React + .NET Assessments
To start, [log in](https://app.codescreen.com/account/login) to CodeScreen, click <strong>Add new assessment</strong>, and select <strong>Custom assessment</strong>.

You can then add the description of your assessment, choose the <strong>Full Stack</strong> category and then choose `React + .NET` for the list of languages.

Once you create an assessment, a private GitHub template repository will be created in the CodeScreen account, and you will be given access.

The template repository will contain two directories, **frontend** and **backend**, and a `README.md` file which will contain the description of the assessment that you added during the setup.

The frontend directory will contain a skeleton `React` project, while the backend directory will contain a skeleton `.NET Core 7` project with an `ASP.NET` server set up. 

You can then update this repository with details of your assessmen, add unit/integration tests, etc.

### Automated test-suite setup

Our full-stack templates are based on the assumption that the task of the assessment is for the candidate to write frontend code which calls an API running on the local backend server to retrieve some data that it then processes/displays. 

Our `GitHub Action` file (see below) will launch the backend server locally and then run Cypress E2E tests against it. The frontend directory in the template repo will include an example Cypress E2E test that calls an example API endpoint on the local backend server.

If you would like to add tests that are automatically run by CodeScreen against each candidate's solution to your assessment, you can add these as unit tests or end-to-end tests.

On the frontend, all unit tests files must use the `Jest` or `Vitest` test framework, and all end-to-end tests must use the `Cypress` E2E test framework.

You can use either `Create React App` or `Vite` as your project build tool for the frontend.

On the backend, all unit tests must use the `Nunit` test framework. The `.csproj` file should be renamed, and the RootNamespace element in this file must be updated to match this new name. The only other updates that should go in to the .csproj file are dependencies required for your assessment.

#### Naming Conventions

- Frontend unit test filenames must end with `.test.js`, `.test.jsx`, `.test.ts`, or `.test.tsx`. Files with names ending in `.hidden.test.js`, `.hidden.test.jsx`, `.hidden.test.ts`, or `.hidden.test.tsx` will be hidden from the candidate.
- Backend unit test filenames must end with `Test`. Files with names ending with `HiddenTest` will be hidden from the candidate.
- End-to-end test filenames must end with `.cy.js` or `.cy.ts`. Files with names ending in `.hidden.cy.js` or .`hidden.cy.ts` will be hidden from the candidate.
- To hide files used by hidden tests, their names must start with "hidden" (case-insensitive), for example: `hiddenFoo.csv`, `HiddenFoo.cs`, etc.

#### GitHub Action

CodeScreen uses GitHub Actions to run automated unit & integration tests. We provide the following GitHub Action file for React + .NET assessments. 

**Note** that this file is added dynamically to the repo of each candidate taking your assessment, so please do not include it in your template repo. This file also cannot be changed.

```yaml
name: React + .NET CI

on: push

defaults:
  run:
    working-directory: frontend/

jobs:

  unitTestsFrontend:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v3

    - name: Install dependencies
      run: npm install

    - name: Run unit tests
      run: npm test -- --passWithNoTests
      env:
        CI: false

  e2eTests:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout
      uses: actions/checkout@v3

    - name: Install dependencies
      run: npm install

    - name: Check ASP.NET backend server exists
      id: check_asp_net_server
      uses: andstor/file-existence-action@v1
      with:
        files: "backend/Properties/launchSettings.json"

    - name: Check Cypress tests exist
      id: check_cypress_tests
      uses: andstor/file-existence-action@v1
      with:
        files: "frontend/cypress/e2e/"

    - name: Setup .NET
      if: steps.check_cypress_tests.outputs.files_exists == 'true' && steps.check_asp_net_server.outputs.files_exists == 'true'
      uses: actions/setup-dotnet@v3
      with:
        dotnet-version: 7.0.x

    - name: Install Dependencies And Build Backend
      if: steps.check_cypress_tests.outputs.files_exists == 'true' && steps.check_asp_net_server.outputs.files_exists == 'true'
      working-directory: backend/
      run: dotnet restore; dotnet build --no-restore

    - name: Launch ASP.NET Server
      if: steps.check_cypress_tests.outputs.files_exists == 'true' && steps.check_asp_net_server.outputs.files_exists == 'true'
      working-directory: backend/
      run: dotnet run &

    - name: Install and run Cypress tests
      uses: cypress-io/github-action@v5
      if: steps.check_cypress_tests.outputs.files_exists == 'true'
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        working-directory: frontend/
        build: npm run build --if-present
        start: npm start
        wait-on: 'http://localhost:3000'
```
