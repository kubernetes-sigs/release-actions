# Release Actions

A set of GitHub actions based on the Kubernetes Release Engineering Tooling

## Installer Actions

The following actions install the Kubernetes Release Engineering tools into 
your runner:

| Action | Description |
| --- | --- |
| [setup-bom](./setup-bom/README.md) | This action enables you to install [bom](https://github.com/kubernetes-sigs/bom) |
| [setup-tejolote](./setup-tejolote/README.md) | This action enables you to install [tejolote](https://github.com/kubernetes-sigs/tejolote) |
| [setup-zeitgeist](./setup-zeitgeist/README.md) | This action enables you to install [zeitgeist](https://github.com/kubernetes-sigs/zeitgeist) |
| [setup-publish-release](./setup-publish-release/README.md) | This action enables you to install [publish-release](https://github.com/kubernetes/release/tree/master/cmd/publish-release) |

## Task-specific Actions

These actions are designed to perform a task using the tools. If there is not a
task action for the tool you are looking for, you can still run it using a 
`runs:` step.

| Action | Description |
| --- | --- |
| [publish-release](./publish-release/README.md) | Cut a new release using [`publish-release github`](https://github.com/kubernetes/release/tree/master/cmd/publish-release) |

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for instructions on how to contribute.
