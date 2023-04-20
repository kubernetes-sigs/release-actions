# setup-tejolote GitHub Action

This action enables you to install [tejolote](https://github.com/kubernetes-sigs/tejolote)

## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: puerco/release-actions/setup-tejolote@main
with:
  tejolote-release: '0.2.0' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_tejolote_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install tejolote and test presence in path
    steps:
      - name: Install tejolote
        uses: puerco/release-actions/setup-tejolote@main
        with:
          tejolote-release: '0.2.0' # optional
      - name: Check install!
        run: tejolote version
```

Example using the default version:

```yaml
jobs:
  test_tejolote_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install tejolote and test presence in path
    steps:
      - name: Install tejolote
        uses: puerco/release-actions/setup-tejolote@main
      - name: Check install!
        run: tejolote version
```

### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `tejolote-release` | `tejolote` version to use instead of the default. |
| `install-dir` | directory to place the `tejolote` binary into instead of the default (`$HOME/.tejolote`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
