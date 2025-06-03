# Polaris Distributions

This repository contains distribution packages for the Polaris Node Manager application, organized by version.

## 🚀 Latest Version: v2.0.1

**Polaris Node Manager v2.0.1** brings significant under-the-hood improvements, focusing on SSH reliability, automated hardware detection, and resource management alignment.

### 🆕 What's New in v2.0.1
- **SSH Overhaul**: Replaced `electron-ssh2` with direct OpenSSH calls for improved stability and security.
- **Automated Hardware Detection**: Integrated `detect_compute_specs.py` for automatic remote hardware detection (CPU, GPU, RAM, Storage), replacing previous manual methods.
- **Enhanced Connection Flow**: Updated SSH connection process to utilize the new Python-based hardware detection.
- **Resource Deletion Verified**: Confirmed compute resource deletion functionality aligns with Firebase API.

### Key Features from v2.0.0 (Still Included)
- **Multi-Machine Management**: Register and manage multiple mining rigs under a single UID
- **Self-Validation System**: Automated server authentication and performance benchmarking
- **Real-time Monitoring**: Live status tracking for all connected mining machines
- **Activity Logging**: Comprehensive logging of mining operations and system events
- **Modern React UI**: Clean, responsive interface built with React and Material-UI Joy
- **Enhanced Cross-platform Support**: Optimized for Windows, macOS, and Linux

## Available Platforms

- **Windows**: Universal ZIP build and traditional installer
- **Linux**: Universal ZIP build (containing AppImage) and direct AppImage
- **MacOS**: Universal ZIP build and traditional DMG installer

## Available Versions

- **[v2.0.1](./v2.0.1/) - Latest Release** ⭐
  - SSH client overhaul for enhanced stability
  - Python-based automatic remote hardware detection
  - Verified compute resource deletion with Firebase API

- **[v2.0.0](./v2/) - Previous Stable Release**
  - Multi-machine management with unified UID support
  - Advanced validation and benchmarking system
  - Modern React-based interface
  - Enhanced monitoring and logging capabilities

- [v1.0.0](./v1/) - Legacy Release
  - Single machine setup and basic monitoring
  - Initial Bittensor network integration

## Download Instructions

### Quick Download (Recommended)

**Latest v2.0.1**: Visit the [Releases](https://github.com/bigideaafrica/polaris_distributions/releases) page and download the latest version for your platform.

### Version-Specific Download

Navigate to the specific version folder:
- **v2.0.1** (Latest): [v2.0.1/](./v2.0.1/)
  - Windows: [v2.0.1/windows](./v2.0.1/windows/)
  - Linux: [v2.0.1/linux](./v2.0.1/linux/)
  - MacOS: [v2.0.1/macos](./v2.0.1/macos/)

- **v2.0.0**: [v2/](./v2/)
- **v1.0.0** (Legacy): [v1/](./v1/)

### Clone Repository

Clone this repository for offline access:
```bash
git clone https://github.com/bigideaafrica/polaris_distributions.git
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
   git clone https://github.com/bigideaafrica/polaris_distributions.git
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

### Minimum Requirements
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 500MB disk space (increased for v2 features)
- **Network**: Stable internet connection
- **Permissions**: Administrator/sudo privileges for installation

### Platform-Specific Requirements

#### Windows
- Windows 10 or later (64-bit)
- .NET Framework 4.8+ (included in installer)
- Windows PowerShell 5.0+

#### Linux
- Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, Debian 11+)
- systemd support (for service management)
- GTK3+ libraries (for GUI)

#### MacOS
- macOS 10.15 (Catalina) or later
- Apple Silicon (M1/M2) and Intel processors supported

### Mining Performance Requirements
- **CPU**: Multi-core processor (4+ cores recommended for v2)
- **RAM**: 8GB+ for optimal multi-machine management
- **GPU**: Optional but recommended (NVIDIA/AMD with current drivers)
- **Network**: Low-latency connection for real-time monitoring

## Key Features Comparison

| Feature | v1.0.0 | v2.0.0 |
|---------|--------|--------|
| Machine Management | Single machine | Multiple machines under one UID |
| User Interface | Basic GUI | Modern React + Material-UI |
| Validation System | Manual setup | Automated self-validation |
| Real-time Monitoring | Basic stats | Live status + activity logs |
| Performance Benchmarking | None | Built-in CPU/GPU scoring |
| Cross-platform | Windows/Linux | Windows/Linux/MacOS |
| Network Monitoring | Basic | Advanced with response times |

## Roadmap

- **v2.0.1** ✅ - SSH overhaul, Python-based hardware detection, resource deletion verified
- **v2.0.0** ✅ - Multi-node management with self-validation
- **v2.1.0** 🔄 - Advanced analytics and reporting dashboard (Planned)
- **v2.2.0** 📋 - API integration and remote management (Planned)
- **v3.0.0** 🚀 - Cloud-based management and mobile app (Planned)

## Build Information

All releases are built using PyInstaller and include necessary dependencies. The Windows installers are created using NSIS, while Linux packages are provided as DEB, RPM, and tar.gz formats.

## License

Polaris Installer is distributed under the [MIT License](https://opensource.org/licenses/MIT).

- 🐛 Issues: [GitHub Issues](https://github.com/bigideaafrica/polaris_distributions/issues) 
