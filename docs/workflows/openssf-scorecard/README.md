# OpenSSF Scorecard

Runs [ossf/scorecard-action](https://github.com/ossf/scorecard-action)

## Usage

> [!NOTE]
> This workflow works with public repositories and private repositories are supported if they have GitHub Advanced Security enabled

```yaml
---
name: OpenSSF Scorecard

on:
  push:
    branches:
      - main
  schedule:
    - cron: "30 6 * * 1"

permissions: {}

jobs:
  openssf-scorecard:
    name: OpenSSF Scorecard
    permissions:
      contents: read
      id-token: write
      security-events: write
    uses: ministryofjustice/actions/.github/workflows/openssf-scorecard.yml@<commit SHA> # <version>
```
