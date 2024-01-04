# setup-publish-release GitHub Action

This action enables you to install
[release-notes](https://github.com/kubernetes/release/tree/master/cmd/release-notes)
in your runner.

## Usage

This action clones the Kubernetes Release Engineering respository and builds
`release-notes` from source, adding it to the runner path.

Add the following entry to your Github workflow YAML file:

```yaml
uses: kubernetes-sigs/release-actions/setup-publish-release@main
```

Example using a pinned version:

```yaml
jobs:
  test_relnotes_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install release-notes
    steps:
      - name: Install release-notes
        uses: kubernetes-sigs/release-actions/setup-release-notes@e9a41ac... 
      - name: Check install!
        run: release-notes --help
```

Example using the default version:

```yaml
jobs:
  test_bom_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install release-notes and test presence in path
    steps:
      - name: Install release-notes
        uses: kubernetes-sigs/release-actions/setup-publish-release@main
      - name: Check install!
        run: release-notes --help
```
