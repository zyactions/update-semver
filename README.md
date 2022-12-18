# Update Semver

![License: MIT][shield-license-mit]
[![CI][shield-ci]][workflow-ci]
[![Ubuntu][shield-platform-ubuntu]][job-runs-on]
[![macOS][shield-platform-macos]][job-runs-on]
[![Windows][shield-platform-windows]][job-runs-on]

A GitHub Action to update floating version tag aliases.

## Features

- Updates floating major and minor version tag aliases for projects that follow the [semantic versioning scheme][semver].
- Fast execution
- Scales to large repositories
- Supports all platforms (Linux, macOS, Windows)
- Does not use external GitHub Actions dependencies

## Usage

### Update aliases based on the current `GITHUB_REF`

```yaml
steps:
  - name: Update Semver
    uses: zyactions/update-semver@v1
```

For example, if `GITHUB_REF` contains the value `refs/tags/v2.3.4`, the tag `v2` will be updated or created to refer to the same hash.

### Update aliases based on a specific tag

```yaml
steps:
  - name: Update Semver
    uses: zyactions/update-semver@v1
    with:
      tag: 'v2.3.4'
```

## Inputs

### `tag`

The name of the target tag or the reference to be used to update the other tags.

For example:

- `v2.3.4`
- `tags/v2.3.4`
- `refs/tags/v2.3.4`

Defaults to `GITHUB_REF` if not specified.

### `prefix`

An optional version prefix like e.g. `v` or `release-v`. Defaults to `v`. 

This value is used when searching for existing major- and minor- version tags and as well during initial tag creation.

### `update-minor`

Enable this option to also update minor version tags. Defaults to `false`.

### `ignore-prerelease`

Enable this option to ignore prerelease versions. Defaults to `true`.

## Outputs

This action does not have any outputs.

## Dependencies

This action does use the following official GitHub Actions dependencies:

- [actions/github-script][actions-github-script]

Internal dependencies:

- [semver-tool][semver-tool] (bundled)

## Versioning

Versions follow the [semantic versioning scheme][semver].

## License

Update Semver Action is licensed under the MIT license.

[actions-github-script]: https://github.com/actions/github-script
[job-runs-on]: https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#jobsjob_idruns-on
[semver]: https://semver.org
[semver-tool]: https://github.com/fsaintjacques/semver-tool
[shield-license-mit]: https://img.shields.io/badge/License-MIT-blue.svg
[shield-ci]: https://github.com/zyactions/update-semver/actions/workflows/ci.yml/badge.svg
[shield-platform-ubuntu]: https://img.shields.io/badge/Ubuntu-E95420?logo=ubuntu\&logoColor=white
[shield-platform-macos]: https://img.shields.io/badge/macOS-53C633?logo=apple\&logoColor=white
[shield-platform-windows]: https://img.shields.io/badge/Windows-0078D6?logo=windows\&logoColor=white
[workflow-ci]: https://github.com/zyactions/update-semver/actions/workflows/ci.yml
