# Version Increment ➕

## Use 📄

```yaml
      - name: Get next version
        uses: george-labs/gh-action-semver-increment@latest
        id: version
        with:
          release_branch: publish
```

### Inputs 📥

| name           | description                                                                                                                                                                                 | required | default  |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------|:---------|
| scheme         | The versioning scheme in-use, either `semver`, `calver` or `conventional_commits`                                                                                                           | No       | `semver` |
| pep440         | Set to `true` for PEP440 compatibility of _pre-release_ versions by making use of the build metadata segment of semver, which maps to local version identifier in PEP440                    | No       | `false`  |
| increment      | The digit to increment, either `major`, `minor` or `patch`, ignored if `scheme` == `calver`                                                                                                 | No       | `patch`  |
| release_branch | Specify a non-default branch to use for the release tag (the one without -pre)                                                                                                              | No       |          |
| use_api        | Use the GitHub API to discover current tags, which avoids the need for a git checkout, but requires `curl` and `jq`                                                                         | No       | `false`  |
| tag_prefix     | Prefix the tag with a string (defaults to empty string).  e.g. if set to `@org/product/` the action will filter by this prefix and return `@org/product/1.2.3` in `prefixed-version` output | No       |          |

### Outputs 📤

| name               | description                                                                                                    |
|:-------------------|:---------------------------------------------------------------------------------------------------------------|
| current-version    | The current latest version detected from the git repositories tags                                             |
| current-v-version  | The current latest version detected from the git repositories tags, prefixed with a `v` character              |
| version            | The incremented version number (e.g. the next version)                                                         |
| v-version          | The incremented version number (e.g. the next version), prefixed with a `v` character                          |
| major-version      | Major number of the incremented version                                                                        |
| minor-version      | Minor number of the incremented version                                                                        |
| patch-version      | Patch number of the incremented version                                                                        |
| pre-release-label  | Pre-release label of the incremented version                                                                   |
| major-v-version    | Major number of the incremented version, prefixed with a `v` character                                         |
| minor-v-version    | Minor number of the incremented version, prefixed with a `v` character                                         |
| patch-v-version    | Patch number of the incremented version, prefixed with a `v` character                                         |
| prefixed-version   | Incremented version calculated, including a `tag_prefix` if specified                                          |
| prefixed-v-version | Incremented version calculated, prefixed with a `v` charatcter, and also including a `tag_prefix` if specified |
