# Github action for testing Java (Maven) code
Checkout, build and test your Java (Maven) code


## Usage example
Create a file `.github/workflows/optional-filename.yml` located in your Github project.

```yaml
name: Current Build

on:
  push:
    branches: [ master, main ]
    paths-ignore:
      - '**.md'
  pull_request:

jobs:
  test_pull_request:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ ubuntu-latest, windows-latest ]
    steps:
      - name: Build and test code
        uses: Frejdh/action-build-and-test@v1.0.0
        env:
          GITHUB_TOKEN: ${{ secrets.REPO_TOKEN }}
        with:
          java-version: 17
          cache-id: v1
          run-integration-tests: true
          test-arguments: >
            "-Dtest.unit.enabled=true"
          integration-test-arguments: >
            "-Dtest.integration.enabled=true"
            "-Dapi-keys.github=$GITHUB_TOKEN"
```
