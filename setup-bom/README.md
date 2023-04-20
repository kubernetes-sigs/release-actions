# setup-bom GitHub Action

This action enables you to install [bom](https://github.com/kubernetes-sigs/bom)

## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: puerco/release-action/setup-bom@main
with:
  bom-release: '0.5.0' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_bom_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install bom and test presence in path
    steps:
      - name: Install bom
        uses: puerco/release-actions/setup-bom@main
        with:
          bom-release: '0.5.0' # optional
      - name: Check install!
        run: bom version
```

Example using the default version:

```yaml
jobs:
  test_bom_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install bom and test presence in path
    steps:
      - name: Install bom
        uses: puerco/release-actions/setup-bom@main
      - name: Check install!
        run: bom version
```

### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `bom-release` | `bom` version to use instead of the default. |
| `install-dir` | directory to place the `bom` binary into instead of the default (`$HOME/.bom`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
