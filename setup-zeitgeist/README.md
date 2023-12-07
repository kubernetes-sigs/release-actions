# setup-zeitgeist GitHub Action

This action enables you to install [zeitgeist](https://github.com/kubernetes-sigs/zeitgeist)


## Usage

This action currently supports GitHub-provided Linux, macOS and Windows runners (self-hosted runners may not work).

Add the following entry to your Github workflow YAML file:

```yaml
uses: cpanato/setup-zeitgeist@main
with:
  zeitgeist-release: '0.4.3' # optional
```

Example using a pinned version:

```yaml
jobs:
  test_zeitgeist_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install zeitgeist and test presence in path
    steps:
      - name: Install zeitgeist
        uses: cpanato/setup-zeitgeist@main
        with:
          zeitgeist-release: '0.4.3' # optional
      - name: Check install!
        run: zeitgeist version
```

Example using the default version:

```yaml
jobs:
  test_zeitgeist_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install zeitgeist and test presence in path
    steps:
      - name: Install zeitgeist
        uses: puerco/release-actions/setup-zeitgeist@main
      - name: Check install!
        run: zeitgeist version
```

If you want to install zeitgeist from its main version by using 'go install' under the hood, you can set 'zeitgeist-release' as 'main'. Once you did that, zeitgeist will be installed via 'go install' which means that please ensure that go is installed.

Example of installing zeitgeist via go install:

```yaml
jobs:
  test_zeitgeist_action:
    runs-on: ubuntu-latest

    permissions: {}

    name: Install zeitgeist via go install
    steps:
      - name: Install go
        uses: actions/setup-go@v3
        with:
          go-version: 1.21
          check-latest: true
      - name: Install zeitgeist
        uses: puerco/release-actions/setup-zeitgeist@main
        with:
          zeitgeist-release: main
      - name: Check install!
        run: zeitgeist version
```

### Optional Inputs

The following optional inputs:

| Input | Description |
| --- | --- |
| `zeitgeist-release` | `zeitgeist` version to use instead of the default. |
| `install-dir` | directory to place the `zeitgeist` binary into instead of the default (`$HOME/.zeitgeist`). |
| `use-sudo` | set to `true` if `install-dir` location requires sudo privs. Defaults to false. |
