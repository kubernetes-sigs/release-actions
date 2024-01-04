# setup-publish-release GitHub Action

This action enables you to install
[publish-release](https://github.com/kubernetes/release/tree/master/cmd/publish-release)

## Usage

This action clones the Kubernetes Release Engineering respository and builds
`publish-release` from source, adding it to the runner path.

Add the following entry to your Github workflow YAML file:

```yaml
uses: kubernetes-sigs/release-actions/setup-publish-release@main
```

Example using a pinned version:

```yaml
jobs:
  test_bom_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install publish release
    steps:
      - name: Install publish-releas
        uses: kubernetes-sigs/release-actions/setup-publish-release@e9a41ac... 
      - name: Check install!
        run: publish-release --help
```

Example using the default version:

```yaml
jobs:
  test_pubrel_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install publish-release and test presence in path
    steps:
      - name: Install publish-release
        uses: kubernetes-sigs/release-actions/setup-publish-release@main
      - name: Check install!
        run: publish-release --help
```
