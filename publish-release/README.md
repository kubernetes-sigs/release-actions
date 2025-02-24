# publish-release

This action is designed to run when a repository gets tagged. It uses
[`publish-release github`](https://github.com/kubernetes/release/tree/master/cmd/publish-release)
to create a new release on GitHub. The action can upload assets to the
releases page and automatically create an SBOM.

## Example Release Cut

Please note that `publish-release` uses the Kubernetes release tooling, this
means that it will look for a tag following [semantic versioning](https://semver.org/)
(eg v1.2.3).

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest

    permissions:
      contents: write # needed to write releases

    steps:
      - name: Publish Release
        uses: kubernetes-sigs/release-actions/publish-release@main
        with:
            assets: "kubernetes.png|starship.toml"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `publish-release-version` | `publish-release` version to use instead of the default. |
| `install-dir` | directory to place the `bom` binary into instead of the default (`$HOME/.publish-release`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
| `install-only` | set to `true` if need only install `publish-release` binary. Defaults to false. |
| `assets` | Assets to upload to the release page. |
| `draft` | Mark the release as draft. Defaults to false. |
| `sbom` | Generate an SBOM from the code. Defaults to true. |
| `sbom_format` | format to use for the SBOM [json|tag-value]. Defaults to "json". |
| `template` | Release template file. |
| `name` | Name for the release. |
