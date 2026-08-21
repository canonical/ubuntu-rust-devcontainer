# How to develop or update this DevContainer

## Prerequisites

To do use this DevContainer development or updates, you need:

1. **[Docker](https://www.docker.com/products/docker-desktop)**, **[Podman](https://podman.io/docs/installation)**, or a [OCI Container-compliant alternative](https://code.visualstudio.com/remote/advancedcontainers/docker-options)) installed and running.
2. **[DevContainer CLI](https://github.com/devcontainers/cli)** to add DevContainer configuration into the development container image.
3. **[Visual Studio Code](https://code.visualstudio.com/)** or [another DevContainer-aware editor](https://containers.dev/supporting) installed on your machine.
4. **[DevContainers plug-ins or extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)** installed in VS Code or similar editor plug-ins or extensions for DevContainer support.

## Getting Started

### 1. Clone this repo

```bash
git clone https://github.com/canonical/ubuntu-rust-devcontainer
```

### 2. Open in VS Code

```bash
cd ubuntu-rust-devcontainer
code .
```

### 3. Edit files in .devcontainer

Edit the .devcontainer/Containerfile to change what is *inside* the DevContainer.  The [Containerfile man page](https://manpages.ubuntu.com/manpages/resolute/man5/Containerfile.5.html) or other documentation can be helpful.

Edit the .devcontainer/devcontainer.json to change the configuration for how the DevContainer is loaded and how it interacts with the host environment.  The [devcontainer.json properties reference](https://containers.dev/implementors/json_reference/) describes what properties can be configured.

### 4. Reopen in Container

When VS Code detects the `.devcontainer` folder, it will prompt you to **"Reopen in Container"**. Click the prompt, or manually run the command:

1. Open the Command Palette (`F1` or `Ctrl+Shift+P`)
2. Select **Dev Containers: Reopen in Container**

VS Code will build the container image (this may take a few minutes the first time) and then reconnect to the running container.

### 5. Verify your environment

Once connected, open a terminal (`Ctrl+Shift+\``) and verify:

```bash
rustc --version
cargo --version
```

Test other tools and ensure that the DevContainer provides the desired functionality.


### 6. Build the finalized DevContainer image

After you have verfified the DevContainer configuration and tooling, build the final DevContainer image:

```bash
devcontainer build --workspace-folder . \
  --image-name ghcr.io/YOUR_GITHUB_USERNAME/my-devcontainer:latest 
```

This step and the following steps use the GitHub Container Registry (ghcr.io) as the example container repository.  This is also why "YOUR_GITHUB_USERNAME" is used.  Please adjust container registry URL and account username as needed.

### 7. Publish the DevContainer image

First login to the container registry where you want to publish the DevContainer:
```bash
docker login ghcr.io -u YOUR_GITHUB_USERNAME
```

Then push the finalize DevContainer image:
```bash
docker push ghcr.io/YOUR_GITHUB_USERNAME/my-devcontainer:latest
```

If you encounter any errors, ensure that your container registry account and credentials have container publishing / writing allowed.


### 8. Use the published DevContainer image

After the DevContainer is published, it can be used in projects by adding the required configuration and using editors that DevContainers:

```bash
cd my_project
mkdir .devcontainer
cat << EOF
{
  "name": "My Dev Container",
  "image": "ghcr.io/YOUR_GITHUB_USERNAME/my-devcontainer:latest"
}
EOF
```


## License

See [LICENSE](LICENSE) for details.
