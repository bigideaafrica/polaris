# Polaris Distributions

This repository contains distribution packages for the Polaris Installer application, organized by version.

## Available Platforms

- **Windows**: Installer executable (.exe) and portable version
- **Linux**: DEB packages (Ubuntu/Debian), RPM packages (Fedora/RHEL/CentOS), and portable tarballs
- **MacOS**: Coming soon

## Available Versions

- [v1.0.0](./v1/) - Initial release with Windows and Linux support

## Download Instructions

You can download the Polaris Installer in three ways:

1. **Direct Download**: Visit the [Releases](https://github.com/BANADDA/polaris_distributions/releases) page and download the latest version for your platform.

2. **Version-Specific Download**: Navigate to the specific version folder and download the installer for your platform:
   - Windows: [v1/windows](./v1/windows/)
   - Linux: [v1/linux](./v1/linux/)

3. **Clone Repository**: Clone this repository and access all versions locally:
   ```
   git clone https://github.com/BANADDA/polaris_distributions.git
   ```

## Quick Installation Guide

### Windows
```cmd
# Download installer (Command Prompt)
curl -L -o PolarisInstaller-Setup.exe https://github.com/BANADDA/polaris_distributions/raw/main/v1/windows/PolarisInstaller-Setup.exe

# Run installer
start PolarisInstaller-Setup.exe
```

### Linux (Debian/Ubuntu)
```bash
# Download DEB package
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_amd64.deb" -o "polaris-installer_1.0.0_amd64.deb"

# Install package
sudo dpkg -i polaris-installer_1.0.0_amd64.deb
sudo apt-get install -f  # Install dependencies if needed
```

### Linux (Fedora/RHEL/CentOS)
```bash
# Download RPM package
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_x86_64.rpm" -o "polaris-installer_1.0.0_x86_64.rpm"

# Install package
sudo rpm -i polaris-installer_1.0.0_x86_64.rpm
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

## System Requirements

### Windows
- Windows 10 or later (64-bit)
- 4GB RAM minimum (8GB recommended)
- 100MB disk space
- Internet connection
- Administrator privileges for installation

### Linux
- Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, etc.)
- 4GB RAM minimum (8GB recommended)
- 100MB disk space
- Internet connection
- sudo privileges for installation (for .deb and .rpm packages)

## Roadmap

- **v1.0.0**: Initial Windows and Linux release
- **v1.1.0**: MacOS support
- **v1.2.0**: Enhanced monitoring capabilities
- **v2.0.0**: Multi-node management

## Build Information

All releases are built using PyInstaller and include necessary dependencies. The Windows installers are created using NSIS, while Linux packages are provided as DEB, RPM, and tar.gz formats.

## License

Polaris Installer is distributed under the [MIT License](https://opensource.org/licenses/MIT). 