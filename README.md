# Polaris Distributions

This repository contains distribution packages for the Polaris Installer application, organized by version.

## Available Versions

- [v1.0.0](./v1/) - Initial release with Windows support

## Download Instructions

You can download the Polaris Installer in three ways:

1. **Direct Download**: Visit the [Releases](https://github.com/BANADDA/polaris_distributions/releases) page and download the latest version for your platform.

2. **Version-Specific Download**: Navigate to the specific version folder (e.g., [v1/windows](./v1/windows/)) and download `PolarisInstaller-Setup.exe` directly.

3. **Clone Repository**: Clone this repository and access all versions locally:
   ```
   git clone https://github.com/BANADDA/polaris_distributions.git
   ```

## Large Files Note

This repository uses Git Large File Storage (Git LFS) to manage the installer files. If you want to clone the entire repository including the large installer files:

1. **Install Git LFS**: If you haven't installed Git LFS, do so first:
   ```
   # For Windows (using Chocolatey)
   choco install git-lfs
   
   # For Linux (Debian/Ubuntu)
   sudo apt install git-lfs
   
   # For macOS (using Homebrew)
   brew install git-lfs
   ```

2. **Clone with LFS**: Then clone the repository:
   ```
   git lfs install
   git clone https://github.com/BANADDA/polaris_distributions.git
   ```

3. **Pull Large Files**: If you've already cloned, run:
   ```
   git lfs pull
   ```

## Distribution Structure

Each version folder contains:
- Platform-specific installers
- README with version-specific information
- Requirements and dependency information
- Release notes and key features

## Roadmap

- **v1.0.0**: Initial Windows release
- **v1.1.0**: Linux support (Ubuntu, Debian)
- **v1.2.0**: Enhanced monitoring capabilities
- **v2.0.0**: Multi-node management

## Build Information

All releases are built using PyInstaller and include necessary dependencies. The Windows installers are created using NSIS.

## License

Polaris Installer is distributed under the [MIT License](https://opensource.org/licenses/MIT). 