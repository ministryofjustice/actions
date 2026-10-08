# Clean Runner

This action frees up space on a GitHub-hosted runner

> [!CAUTION]
> The steps performed in this action are destructive, please review before using!

Standard GitHub-hosted runners are only guaranteed 14GB of SSD storage ([source](https://docs.github.com/en/actions/using-github-hosted-runners/using-github-hosted-runners/about-github-hosted-runners#standard-github-hosted-runners-for-public-repositories)), this action removes bundled software as discussed in [this](https://github.com/actions/runner-images/issues/2840) GitHub issue

> [!TIP]
> This action is useful when working with large container images

## Inputs

| Input                               | Default | Required | Description                                  |
| :---------------------------------- | :-----: | :------: | :------------------------------------------- |
| `confirm`                           | `false` |  `true`  | Confirm that you want to remove the software |
| `remove_opt_google`                 | `true`  |  `true`  | Remove `/opt/google` (370MB)                 |
| `remove_opt_hostedtoolcache`        | `true`  |  `true`  | Remove `/opt/hostedtoolcache` (5.1GB)        |
| `remove_opt_microsoft`              | `true`  |  `true`  | Remove `/opt/microsoft` (778MB)              |
| `remove_opt_pipx`                   | `true`  |  `true`  | Remove `/opt/pipx` (534MB)                   |
| `remove_usr_lib_firefox`            | `true`  |  `true`  | Remove `/usr/lib/firefox` (266MB)            |
| `remove_usr_lib_google_cloud_sdk`   | `true`  |  `true`  | Remove `/usr/lib/google-cloud-sdk` (951MB)   |
| `remove_usr_lib_llvm_16`            | `true`  |  `true`  | Remove `/usr/lib/llvm-16` (588MB)            |
| `remove_usr_lib_llvm_17`            | `true`  |  `true`  | Remove `/usr/lib/llvm-17` (584MB)            |
| `remove_usr_lib_llvm_18`            | `true`  |  `true`  | Remove `/usr/lib/llvm-18` (731MB)            |
| `remove_usr_local_julia`            | `true`  |  `true`  | Remove `/usr/local/julia*` (991MB)           |
| `remove_usr_local_lib_android`      | `true`  |  `true`  | Remove `/usr/local/lib/android` (9.5GB)      |
| `remove_usr_local_lib_node_modules` | `true`  |  `true`  | Remove `/usr/local/lib/node_modules` (464M)  |
| `remove_usr_local_share_chromium`   | `true`  |  `true`  | Remove `/usr/local/share/chromium` (598MB)   |
| `remove_usr_local_share_powershell` | `true`  |  `true`  | Remove `/usr/local/share/powershell` (1.3GB) |
| `remove_usr_share_dotnet`           | `true`  |  `true`  | Remove `/usr/share/dotnet` (479M)            |
| `remove_usr_share_miniconda`        | `true`  |  `true`  | Remove `/usr/share/miniconda` (737MB)        |
| `remove_usr_share_swift`            | `true`  |  `true`  | Remove `/usr/share/swift` (2.8GB)            |

## Usage

> [!NOTE]
> To run the cleanup operation, you will need to explicitly set `confirm: true`

```yaml
- name: Clean Actions Runner
  id: clean_actions_runner
  uses: ministryofjustice/actions/clean-runner@<commit SHA> # <version>
  with:
    confirm: true
```

To retain a specific piece of software, set its input to `false`, for example:

```yaml
- name: Clean Actions Runner
  id: clean_actions_runner
  uses: ministryofjustice/actions/clean-runner@<commit SHA> # <version>
  with:
    confirm: true
    remove_opt_hostedtoolcache: false
```

Using the default options should reclaim about 29GB
