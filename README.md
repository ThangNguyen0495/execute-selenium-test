# Selenium Workflow Action

A custom GitHub Action designed to run Selenium tests with Maven. This action provides flexibility in configuring Java versions, executing custom Maven commands, and generating test reports. It's ideal for integrating Selenium tests into your CI/CD pipeline on GitHub Actions.

## Inputs

### `java_version` (Optional)
- **Description**: The version of Java to install.
- **Default**: `22`
- **Required**: No

### `test_name` (Required)
- **Description**: The name of the test suite. This will be used when uploading test reports.
- **Required**: Yes

### `scripts` (Required)
- **Description**: The Maven commands to execute the tests. This allows you to run customized test commands.
- **Required**: Yes

---

## Example Workflow

Here's an example of how to use this action in your workflow:

```yaml
name: Run Selenium Tests

on:
  push:
    branches:
      - main

jobs:
  selenium-tests:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Run Selenium Tests with Maven
        uses: ThangNguyen0495/execute-selenium-test@v1.0.0
        with:
          java_version: '22'
          test_name: 'MyTestSuite'
          scripts: 'mvn test -DsuiteFile=testng.xml'
