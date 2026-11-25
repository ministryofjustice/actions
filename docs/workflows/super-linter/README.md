# Super-Linter

Runs [super-linter/super-linter](https://github.com/super-linter/super-linter)

## Inputs

|          Input           |   Type   | Required | Default |
| :----------------------: | :------: | :------: | :-----: |
| `super-linter-variables` | `string` | `false`  | `"{}"`  |

## Usage

```yaml
---
name: Super-Linter

on:
  pull_request:
    branches:
      - main

permissions: {}

jobs:
  super-linter:
    name: Super-Linter
    permissions:
      contents: read
      issues: write
      packages: read
      pull-requests: write
      statuses: write
    uses: ministryofjustice/actions/.github/workflows/super-linter.yml@<commit SHA> # <version>
```

### Configuring Super-Linter Settings

The `super-linter-variables` input passes environment variables through to Super-Linter. By default, all supported validators are enabled except Trivy, which is disabled because it is not permitted at MOJ.

To disable additional validators, set their `VALIDATE_*` variables to `false`. Do not set validator variables to `true`: Super-Linter does not support mixing `true` and `false` validator settings. Other settings, such as `ENABLE_GITHUB_ACTIONS_STEP_SUMMARY`, can still be configured through this input.

```yaml
jobs:
  super-linter:
    name: Super-Linter
    permissions:
      contents: read
      issues: write
      packages: read
      pull-requests: write
      statuses: write
    uses: ministryofjustice/actions/.github/workflows/super-linter.yml@<commit SHA> # <version>
    with:
      super-linter-variables: |
        {
          "VALIDATE_X": false,
          "KEY": "value"
        }
```
