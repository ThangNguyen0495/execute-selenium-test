# Selenium Workflow Action

This custom GitHub Action is designed to run Selenium tests using Maven. It allows for flexible configuration, including specifying the Java version, downloading artifacts, switching branches, and using custom Maven commands.

## Features

- **Java Version Support**: Install and use a specified version of Java (default is `22`).
- **Artifact Download**: Optionally download an artifact containing the test source code.
- **Branch Switching**: Optionally switch to a different branch before running tests.
- **Custom Maven Commands**: Run custom Maven commands to execute tests.
- **Automated Test Execution**: Easily configure and run Selenium tests with various parameters.

## Inputs

| Input Name    | Description                                                           | Required | Default |
|---------------|-----------------------------------------------------------------------|----------|---------|
| `java_version`| The version of Java to install.                                        | false    | `22`    |
| `artifact`    | The artifact to download, containing the test source code.             | false    |         |
| `test_config` | The test configuration file to use.                                    | false    |         |
| `test_name`   | The name of the test suite.                                            | true     |         |
| `branch_name` | The branch name to switch to.                                          | false    |         |
| `scripts`     | The Maven commands to execute the test.                                | false    |         |

## Usage

To use this action in your GitHub workflow, include the following steps:

```yaml
name: Run Selenium Tests

on:
  workflow_dispatch:

jobs:
  selenium-tests:
    runs-on: ubuntu-latest

    steps:
    - name: Run Selenium Workflow
      uses: ThangNguyen0495/execute-selenium-test@v1.0.0
      with:
        java_version: '22'             # Optional: Specify Java version
        artifact: 'your-artifact-name' # Optional: Name of the artifact to download
        test_config: 'testng.xml'      # Optional: Path to the test configuration file
        test_name: 'MyTestSuite'       # Required: Name of the test suite
        branch_name: 'main'            # Optional: Branch to switch to
        scripts: 'mvn clean test'      # Optional: Custom Maven commands to run the tests
