# setup-krel GitHub Action

This action installs [krel](https://github.com/kubernetes/release/tree/master/cmd/krel) (Kubernetes Release Toolbox) in your GitHub Actions runner.

## Usage

This action installs the binary using `go install` command. Add the following entry to your Github workflow YAML file:

```yaml
- uses: kubernetes-sigs/release-actions/setup-krel@main
```

### Basic Example

```yaml
jobs:
  test_setup_krel:
    runs-on: ubuntu-latest
    permissions: {}
    name: Install krel
    steps:
      - name: Install krel
        uses: kubernetes-sigs/release-actions/setup-krel@main
      - name: Verify installation
        run: krel version
```

### Example with Pinned Version (Recommended for Production)

```yaml
jobs:
  test_setup_krel:
    runs-on: ubuntu-latest
    permissions: {}
    name: Install krel
    steps:
      - name: Install krel
        uses: kubernetes-sigs/release-actions/setup-krel@e9a41ac  # Replace with a specific commit SHA
      - name: Verify installation
        run: krel version
```

### Example Using the Installation Path Output

```yaml
jobs:
  test_setup_krel:
    runs-on: ubuntu-latest
    permissions: {}
    name: Install and use krel
    steps:
      - name: Install krel
        id: krel-installation
        uses: kubernetes-sigs/release-actions/setup-krel@main
      
      - name: Show krel path
        run: echo "krel is installed at ${{ steps.krel-installation.outputs.krel-path }}"
      
      - name: Use krel from path
        run: |
          KREL_BIN="${{ steps.krel-installation.outputs.krel-path }}"
          "$KREL_BIN" version
```

## Outputs

| Output      | Description                            |
|-------------|----------------------------------------|
| `krel-path` | Full path to the installed krel binary |
