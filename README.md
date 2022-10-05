# Utbot Action

You can use this GitHub Action to create pull requests tests and code analysis info to your repository

## Content

- [Inputs](#inputs)
- [Installation](#installation)
- [Examples](#examples)

## Inputs

All inputs are required
add_tests, refresh_tests, tests_scope, scope_path
| Name | Type | Description | Required |
| --- | --- | --- | --- |
| `add_tests` | 'true' / 'false' | Add tests to pull request  | `Yes` |
| `refresh_tests` | 'true' / 'false' | Delete old tests in pull request | `Yes` |
| `utbot_version` | xxxx.xx[.xx] | UTBot version to run  | `Yes` |
| `scope` |  `project` / `directory` / `file` | Testing scope | `Yes` |
| `path` | Realtive path string | `directory` or `file` path | `No` for the `project`, `Yes` for the rest |

## Installation

* `Settings > Actions > Allow GitHub Actions to create and approve pull requests`
* `permissions: write-all` line at action before using Utbot Action
* create the file `.github/workflows/run-utbot.yml` with context from the section below


## Examples

```yml
name: "Run UTBotCpp-action"

on:
  workflow_dispatch:
    
jobs:
  build:
    runs-on: ubuntu-latest
    permissions: write-all
    steps:
    - name: UTBot code analysis
      uses: UnitTestBot/UTBotCpp-action@test-1.0.26
      with:
        add_tests: 'true'
        refresh_tests: 'true'
        utbot_version: '2022.10.3'
        scope: 'project'
# for individual file:
#       scope: 'file'
#       path: 'src/main.c'
```
