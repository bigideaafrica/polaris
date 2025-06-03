# Polaris Node Manager v2.0.1 - macOS

Welcome to the macOS distribution of **Polaris Node Manager v2.0.1**! This version includes SSH enhancements using the native OpenSSH client and automated hardware detection via a Python script. This package provides a universal ZIP build and a traditional DMG installer.

## 📦 Available Downloads (v2.0.1)

### macOS Build (Recommended)
- **polaris-node-manager-macos-v2.0.1.zip** - Universal macOS application bundle (~895MB expected)
- **Installation**: Extract ZIP and run the `Polaris Node Manager.app` inside.

### DMG Installer (Alternative)
- **PolarisNodeManager-v2.0.1.dmg** - Traditional macOS installer (~95MB expected)
- **Installation**: Drag to Applications folder.

*Note: Exact file sizes for v2.0.1 are estimates and will be confirmed upon release.*

## 🆕 What's New in v2.0.1 for macOS
- **SSH Overhaul**: Utilizes the native macOS OpenSSH client for connections, replacing `electron-ssh2`.
- **Automated Hardware Detection**: Uses a Python script (`detect_compute_specs.py`) for remote hardware detection. Requires Python 3.x to be available (usually pre-installed on macOS or easily installable via Homebrew). Polaris Node Manager manages this script's execution.
- **Verified Resource Deletion**: Confirmed compute resource deletion functionality aligns with Firebase API.

## 🔧 System Requirements

### Minimum Requirements
- **OS**: macOS 10.15 (Catalina) or later.
- **Python 3.x**: Recommended for full functionality of `detect_compute_specs.py`. (Check with `python3 --version`. Install via Homebrew if needed: `brew install python`)
- **OpenSSH Client**: Included with macOS by default.
- **Architecture**: Universal binary supports Apple Silicon (M1/M2) and Intel Macs.
- **RAM**: 4GB minimum (8GB recommended).
- **Storage**: 2GB free disk space (for ZIP build extraction and operation).

### Recommended Configuration
- **OS**: macOS 12 (Monterey) or later.
- **RAM**: 8GB+ for managing multiple machines.
- **Storage**: 2GB+ free space.

## 🚀 Installation Instructions (v2.0.1)

### Method 1: ZIP Build (Recommended)

#### Download and Extract
```bash
# Download macOS build v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/macos/polaris-node-manager-macos-v2.0.1.zip" -o "polaris-node-manager-macos-v2.0.1.zip"

# Extract the file to a specific directory
unzip polaris-node-manager-macos-v2.0.1.zip -d polaris-node-manager-v2.0.1
cd polaris-node-manager-v2.0.1

# Open the application (assuming it's named Polaris Node Manager.app inside)
open "Polaris Node Manager.app"
```
*The exact name of the .app bundle inside the ZIP might vary slightly; adjust the `open` command if needed based on the extracted file name.*

#### Alternative Manual Extraction
1. **Download** `polaris-node-manager-macos-v2.0.1.zip`.
2. **Double-click** the ZIP to extract it into a folder (e.g., `polaris-node-manager-v2.0.1`).
3. **Navigate** to the folder and **double-click** `Polaris Node Manager.app`.

### Method 2: DMG Installer

#### Download and Install
```bash
# Download DMG v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/macos/PolarisNodeManager-v2.0.1.dmg" -o "PolarisNodeManager-v2.0.1.dmg"

# Open DMG (will mount automatically)
open "PolarisNodeManager-v2.0.1.dmg"

# Drag "Polaris Node Manager.app" to Applications folder when DMG opens
```

## 📂 File Structure
(Similar to v2.0.0, filenames inside ZIP/DMG will reflect v2.0.1 where applicable)

## 🏃‍♂️ Running the Application
(Process is the same as v2.0.0, but note the SSH and hardware detection improvements during machine setup)

## 🚨 Troubleshooting (v2.0.1 Specific)

#### SSH Connection Issues
- **Native OpenSSH**: Since v2.0.1 uses the system's OpenSSH, ensure your macOS network settings and any firewalls (like Little Snitch or the built-in one if configured restrictively) allow outgoing SSH from the Polaris app.
- **Remote SSH Server**: Confirm the mining rig's SSH server configuration.

#### Hardware Detection Not Working (`detect_compute_specs.py` issues)
- **Verify Python 3.x**: Open Terminal and type `python3 --version`. If not found or an old version, install/update it (e.g., via Homebrew: `brew install python`).
- **Script Execution**: The Python script is executed on the remote machine via SSH. Issues could stem from remote machine permissions or environment if highly restricted.

(General troubleshooting for Gatekeeper, Keychain, etc., remains similar to v2.0.0)

## 📞 Support
(Contact methods remain the same)

---

**Experience enhanced stability on macOS with Polaris Node Manager v2.0.1!** Follow the installation instructions for the latest version. 🍎🚀 