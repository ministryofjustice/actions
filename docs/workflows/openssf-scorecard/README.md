# OpenSSF Scorecard

Runs [ossf/scorecard-action](https://github.com/ossf/scorecard-action)

## Usage

> [!NOTE]
> This workflow runs on public and private repositories. Private repositories need GitHub Advanced Security enabled for the SARIF results to be uploaded to code scanning.
>
> Results are published to the OpenSSF Scorecard API only for public repositories. For private repositories, publishing is disabled to avoid sending results about private code to the public API.

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
      actions: read
      checks: read
      contents: read
      id-token: write
      issues: read
      pull-requests: read
      security-events: write
    uses: ministryofjustice/actions/.github/workflows/openssf-scorecard.yml@<commit SHA> # <version>
```
