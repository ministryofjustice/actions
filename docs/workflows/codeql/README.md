# CodeQL

Runs [github/codeql-action/analyze](https://github.com/github/codeql-action/tree/main/analyze)

## Inputs

|    Input    |   Type   | Required |     Default     |
| :---------: | :------: | :------: | :-------------: |
| `languages` | `string` | `false`  | `'["actions"]'` |

## Usage

```yaml
---
name: CodeQL

on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

permissions: {}

jobs:
  codeql:
    name: CodeQL
    permissions:
      actions: read
      contents: read
      security-events: write
    uses: ministryofjustice/actions/.github/workflows/codeql.yml@<commit SHA> # <version>
```

### Including Languages

> [!NOTE]
> You must include `actions`

```yaml
jobs:
  codeql-analysis:
    name: CodeQL Analysis
    permissions:
      actions: read
      contents: read
      security-events: write
    uses: ministryofjustice/actions/.github/workflows/codeql.yml@<commit SHA> # <version>
    with:
      languages: '["actions", "python"]'
```
