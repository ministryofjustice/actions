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

The `super-linter-variables` input passes environment variables through to Super-Linter. The reusable workflow does not set validator defaults, so an empty object (`{}`) uses Super-Linter's defaults.

Super-Linter supports two ways to select validators: set `VALIDATE_*` variables to `false` to disable specific validators, or set them to `true` to run only the validators explicitly set to `true`. Do not mix `true` and `false` values.

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
