# Ubuntu Rust DevContainer

A ready-to-use [Dev Container](https://containers.dev/) for Rust software development on Ubuntu 26.04.

## What's Included

### Base Image

- **Ubuntu 26.04** base image

### Rust Toolchain

- Rust 1.93 (compiler, standard library, documentation, and source)
- Cargo (package manager)
- rust-analyzer (IDE support via VS Code extension)
- Clippy (linter)
- Rustfmt (formatter)
- Miri (interpreter for detecting undefined behavior)
- cargo-auditable (for auditable builds)
- cargo-audit (check auditable binaries for vulnerabilities)
- cargo-deny (lint project dependency graph)
- cargo-vet (ensure dependencies have been audited by a trusted entity)
- cargo-mutants (mutation testing tool for Rust)
- cargo-outdated (display when dependencies have newer versions available)

### Build Tools

- GCC / build-essential
- Clang + LLD (alternative compiler/linker)
- pkg-config
- OpenSSL development libraries
- Make
- [Just](https://github.com/casey/just) (command runner)

### Developer Utilities

- Git
- Vim
- [Helix](https://helix-editor.com/) (`hx`) — terminal editor
- [Ripgrep](https://github.com/BurntSushi/ripgrep) (`rg`) — fast search
- [Hyperfine](https://github.com/sharkdp/hyperfine) — benchmarking tool
- [Bacon](https://github.com/Canop/bacon) — background Rust code checker
- [xh](https://github.com/ducaale/xh) — HTTP client
- curl

### Shells

- Fish (default entrypoint)
- Bash

### Forwarded Ports

Ports **8000** and **8080** are forwarded by default, useful for web servers and APIs.

### VS Code Extensions

- [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) — Rust language support

## Prerequisites

To use this Dev Container, you need:

1. **[Docker](https://www.docker.com/products/docker-desktop)**, **[Podman](https://podman.io/docs/installation)**, (or a [OCI Container-compliant alternative](https://code.visualstudio.com/remote/advancedcontainers/docker-options)) installed and running.
2. **[Visual Studio Code](https://code.visualstudio.com/)** or [another DevContainer-aware editor](https://containers.dev/supporting) installed on your machine.
3. **[DevContainers plug-ins or extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)** installed in VS Code or similar editor plug-ins or extensions for DevContainer support.

## Getting Started

### 1. Add DevContainer configuration to the project
```bash
cd my_project
mkdir .devcontainer
cat << EOF > devcontainer.json
{
    "name": "Ubuntu Rust DevContainer",
    "image": "ghcr.io/canonical/ubuntu-26.04-rust-1.93-devcontainer:latest"
}
EOF
```

### 2. Open in VS Code (or your preferred editor)

```bash
code .
```

### 3. Reopen in Container

When VS Code detects the `.devcontainer` folder, it will prompt you to **"Reopen in Container"**. Click the prompt, or manually run the command:

1. Open the Command Palette (`F1` or `Ctrl+Shift+P`)
2. Select **Dev Containers: Reopen in Container**

VS Code will build the container image (this may take a few minutes the first time) and then reconnect to the running container.

### 4. Examine the container environment

Once connected, open a terminal (`Ctrl+Shift+\``) and verify:

```bash
rustc --version
cargo --version
```


### 5. Start coding

You can now create a new Rust project or open an existing one:

```bash
cargo init my-project
cd my-project
cargo run
```

## How It Works

The Dev Containers extension uses the files in the `.devcontainer` directory:

- **`devcontainer.json`** — Configuration for the container name, extensions, forwarded ports, and runtime arguments.

- [Rust documentation](https://doc.rust-lang.org/)

## License

See [LICENSE](LICENSE) for details.
