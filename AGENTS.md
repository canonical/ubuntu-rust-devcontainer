# Project Overview
ubuntu-rust-devcontainer is the configuration for a ready-to-use [DevContainer](https://containers.dev/) for Rust software development on Ubuntu.  There are two variants of the the Ubuntu Rust DevContainer:
* general-purpose Rust development - designed for most Rust software development work
* Ubuntu distro Rust development - includes all general-purpose Rust development tools plus additional tools for Ubuntu distribution development work

Usually, DevContainers will only be made for Ubuntu LTS releases.  Interim release Ubuntu Rust DevContainers will be created and published as need and circumstances require.

## Git Branches
`main` - the most recent Ubuntu LTS version with the default Rust toolchain for that release; this is the "default" Ubuntu Rust DevContainer that most developers should use.
`ubuntu-26.04-rust-1.93` - the general-purpose Ubuntu Rust DevContainer based on Ubuntu 26.04 LTS and Rust 1.93.1
`ubuntu-26.04-rust-1.93-distro` - the Ubuntu distro Ubuntu Rust DevContainer based on Ubuntu 26.04 LTS and Rust 1.93.1

## Project Structure
`.devcontainer/devcontainer.json` - configuration used to build and load a DevContainer in a supporting editor or IDE
`.devcontainer/Containerfile` - OCI-compliant container configuration to build the DevContainer image
`DEVELOP.md` - instructions about how to develop, update, and publish the DevContainer
`LICENSE` - the license file for this project
`README.md` - descriptive listing of the tools and features of the DevContainer; this will vary based on the DevContainer variant and git branch
