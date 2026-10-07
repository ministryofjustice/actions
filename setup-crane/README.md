# Set Up Crane

This action installs Google's [crane](https://github.com/google/go-containerregistry/tree/main/cmd/crane)

## Inputs

| Input          | Type     | Required | Default               |
| -------------- | -------- | -------- | --------------------- |
| `github-token` | `string` | false    | `${{ github.token }}` |
| `version`      | `string` | false    | `latest`              |

## Usage

```yaml
- name: Set Up crane
  id: setup_crane
  uses: ministryofjustice/action-setup-crane@<commit SHA> # <version>

- name: Run crane
  id: run_crane
  run: |
    crane ...
```

Specifying a version

```yaml
- name: Set Up crane
  id: setup_crane
  uses: ministryofjustice/action-setup-crane@<commit SHA> # <version>
  with:
    version: v0.20.3
```
