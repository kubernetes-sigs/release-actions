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
      - name: Install publish-release
        uses: kubernetes-sigs/release-actions/setup-publish-release@main

      - name: Publish Release
        uses: kubernetes-sigs/release-actions/publish-release@main
        with:
            assets: "kubernetes.png|starship.toml"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

