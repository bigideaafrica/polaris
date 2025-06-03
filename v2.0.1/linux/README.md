# Polaris Node Manager v2.0.1 - Linux

Welcome to the Linux distribution of **Polaris Node Manager v2.0.1**! This version includes SSH enhancements and automated hardware detection. This package provides a universal ZIP build (containing an AppImage) and a direct AppImage download.

## 📦 Available Downloads (v2.0.1)

### Linux Build (Recommended)
- **polaris-node-manager-linux-v2.0.1.zip** - Universal Linux application bundle (~405MB expected)
- **Installation**: Extract ZIP and run the `polaris-node-manager.AppImage` inside.

### AppImage Alternative
- **PolarisNodeManager-v2.0.1.AppImage** - Traditional AppImage format (~100MB expected)
- **Installation**: Download, make executable, and run.

*Note: Exact file sizes for v2.0.1 are estimates and will be confirmed upon release.*

## 🆕 What's New in v2.0.1 for Linux
- **SSH Overhaul**: Replaced `electron-ssh2` with direct OpenSSH calls. Requires `openssh-client` to be installed on the system.
- **Automated Hardware Detection**: Uses a Python script (`detect_compute_specs.py`) for remote hardware detection. Requires Python 3.x to be installed and accessible in PATH. Polaris Node Manager manages this script's execution via the new SSH mechanism.
- **Verified Resource Deletion**: Confirmed compute resource deletion functionality aligns with Firebase API.

## 🔧 System Requirements

### Minimum Requirements
- **OS**: Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, Debian 11+)
- **Python 3.x**: Required for `detect_compute_specs.py`.
- **OpenSSH Client**: `openssh-client` package (or equivalent) must be installed.
- **Architecture**: 64-bit (x86_64) or ARM64 (AppImage inside ZIP may be x64 by default, check release notes for ARM64 AppImage if needed).
- **RAM**: 4GB minimum (8GB recommended).
- **Storage**: 1GB free disk space (for ZIP build extraction).
- **Display**: X11 or Wayland with GTK3+ support.

### Required Dependencies (General GUI)
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install -y libgtk-3-0 libnotify4 libnss3 libxss1 libxtst6 xdg-utils python3 openssh-client

# Fedora/RHEL/CentOS
sudo dnf install -y gtk3 libnotify nss libXss libXtst xdg-utils python3 openssh-clients

# Arch Linux
sudo pacman -Syu --noconfirm gtk3 libnotify nss libxss libxtst xdg-utils python openssh
```

## 🚀 Installation Instructions (v2.0.1)

### Method 1: ZIP Build (Recommended)

#### Download and Extract
```bash
# Download Linux build v2.0.1
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/linux/polaris-node-manager-linux-v2.0.1.zip"

# Extract the file to a specific directory
unzip polaris-node-manager-linux-v2.0.1.zip -d polaris-node-manager-v2.0.1
cd polaris-node-manager-v2.0.1

# Make executable and run (assuming AppImage inside is named polaris-node-manager.AppImage)
chmod +x ./polaris-node-manager.AppImage 
./polaris-node-manager.AppImage
```
*The exact name of the AppImage inside the ZIP might vary slightly, adjust `chmod +x` and run commands accordingly based on the extracted file name.*

### Method 2: Direct AppImage

#### Download and Run
```bash
# Download AppImage v2.0.1 directly (ensure it matches your architecture if separate AppImages are provided)
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/linux/PolarisNodeManager-v2.0.1.AppImage"

# Make executable
chmod +x PolarisNodeManager-v2.0.1.AppImage

# Run the application
./PolarisNodeManager-v2.0.1.AppImage
```

## 📂 File Structure
(Similar to v2.0.0, filenames inside ZIP/AppImage will reflect v2.0.1 where applicable)

## 🏃‍♂️ Running the Application
(Process is the same as v2.0.0, but note the SSH and hardware detection improvements during machine setup)

## 🚨 Troubleshooting (v2.0.1 Specific)

#### SSH Connection Issues
- **Verify OpenSSH Client**: Ensure `openssh-client` is installed. Use `ssh -V` to check.
- **Firewall**: Check `ufw`, `firewalld`, or other firewalls for rules blocking outgoing SSH.
- **Remote SSH Server**: Confirm the mining rig's SSH server is active and correctly configured.

#### Hardware Detection Not Working (`detect_compute_specs.py` issues)
- **Verify Python 3.x**: Ensure Python 3.x is installed (`python3 --version`) and accessible in your system's PATH.
- **Script Execution**: The Python script is executed on the remote machine via SSH. Issues could stem from remote machine permissions or environment for Python scripts if highly restricted.

#### AppImage Issues
- **FUSE**: Some systems might need FUSE installed to run AppImages: `sudo apt install libfuse2` (Debian/Ubuntu) or equivalent for other distributions.

(General troubleshooting remains similar to v2.0.0)

## 📞 Support
(Contact methods remain the same)

---

**Ready for a more stable and automated mining management experience on Linux?** Follow the installation instructions for v2.0.1! 🐧🚀 