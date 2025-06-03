# Polaris Node Manager v2.0.1 - Windows

Welcome to the Windows distribution of **Polaris Node Manager v2.0.1**! This version includes SSH enhancements and automated hardware detection. This package contains optimized Windows ZIP builds and traditional installers.

## 📦 Available Downloads (v2.0.1)

### Windows Build (Recommended)
- **polaris-node-manager-windows-v2.0.1.zip** - Universal Windows application bundle (~175MB expected)
- **Installation**: Extract ZIP and run `polaris-node-manager.exe`

### Windows Installer (Alternative)
- **PolarisNodeManagerSetup-v2.0.1.exe** - Traditional Windows installer (~75MB expected)
- **Installation**: Automatic with Windows integration

*Note: Exact file sizes for v2.0.1 are estimates and will be confirmed upon release.*

## 🆕 What's New in v2.0.1 for Windows
- **SSH Overhaul**: Replaced `electron-ssh2` with direct OpenSSH calls. Requires the Windows OpenSSH client feature to be enabled (usually on by default in modern Windows 10/11).
- **Automated Hardware Detection**: Uses a Python script (`detect_compute_specs.py`) for remote hardware detection. Polaris Node Manager will manage this script's execution via the new SSH mechanism.
- **Verified Resource Deletion**: Confirmed compute resource deletion functionality aligns with Firebase API.

## 🔧 System Requirements

### Minimum Requirements
- **OS**: Windows 10 (build 1903) or Windows 11 (64-bit)
- **OpenSSH Client**: Windows OpenSSH Client feature must be enabled. (Check via Settings > Apps > Optional features).
- **RAM**: 4GB minimum (8GB recommended)
- **Storage**: 1GB free disk space (for ZIP build extraction)
- **Network**: Internet connection required

### Recommended Configuration
- **OS**: Windows 11 (latest updates)
- **RAM**: 8GB+ for managing multiple machines
- **Storage**: 2GB+ free space (for logs and cache)

## 🚀 Installation Instructions (v2.0.1)

> **💡 Which Command Interface Should I Use?**
> (Same as v2.0.0 - Command Prompt for `curl`/`tar`, PowerShell for `Invoke-WebRequest`/`Expand-Archive`)

### Method 1: ZIP Build (Recommended)

#### Option A: Command Prompt (cmd.exe)
```cmd
REM Download Windows build v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/polaris-node-manager-windows-v2.0.1.zip" -o "polaris-node-manager-windows-v2.0.1.zip"

REM Extract using built-in tar (Windows 10+)
tar -xf polaris-node-manager-windows-v2.0.1.zip -C polaris-node-manager-v2.0.1

REM Navigate to extracted folder
cd polaris-node-manager-v2.0.1

REM Run the application
polaris-node-manager.exe
```

#### Option B: PowerShell
```powershell
# Download Windows build v2.0.1
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/polaris-node-manager-windows-v2.0.1.zip" -OutFile "polaris-node-manager-windows-v2.0.1.zip"

# Extract the ZIP file
Expand-Archive -Path "polaris-node-manager-windows-v2.0.1.zip" -DestinationPath ".\polaris-node-manager-v2.0.1"

# Navigate to extracted folder
cd polaris-node-manager-v2.0.1

# Run the application
.\polaris-node-manager.exe
```

#### Option C: Manual Download (Easiest)
1. **Download** `polaris-node-manager-windows-v2.0.1.zip`.
2. **Right-click** the ZIP file → "Extract All..." into a folder like `polaris-node-manager-v2.0.1`.
3. **Navigate** to the extracted folder and **double-click** `polaris-node-manager.exe`.

### Method 2: Traditional Installer

#### Option A: Command Prompt (cmd.exe)
```cmd
REM Download installer v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/PolarisNodeManagerSetup-v2.0.1.exe" -o "PolarisNodeManagerSetup-v2.0.1.exe"

REM Run installer (requires admin privileges)
"PolarisNodeManagerSetup-v2.0.1.exe"
```

#### Option B: PowerShell
```powershell
# Download installer v2.0.1
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/PolarisNodeManagerSetup-v2.0.1.exe" -OutFile "PolarisNodeManagerSetup-v2.0.1.exe"

# Run with administrator privileges
Start-Process -FilePath ".\PolarisNodeManagerSetup-v2.0.1.exe" -Verb RunAs
```

## 📂 File Structure
(Similar to v2.0.0, filenames inside ZIP/Installer will reflect v2.0.1 where applicable)

## 🏃‍♂️ Running the Application
(Process is the same as v2.0.0, but note the SSH and hardware detection improvements during machine setup)

## 🚨 Troubleshooting (v2.0.1 Specific)

#### SSH Connection Issues
- **Verify OpenSSH Client**: Ensure "OpenSSH Client" is listed and installed under Windows Settings > Apps > Optional features. If not, add it.
- **Firewall**: Check that your firewall (Windows Defender Firewall or third-party) isn't blocking outgoing OpenSSH connections from `polaris-node-manager.exe` or `ssh.exe`.
- **Remote SSH Server**: Ensure the SSH server on the mining rig is configured correctly and allows connections.

#### Hardware Detection Not Working
- The automated hardware detection relies on the new SSH mechanism and the `detect_compute_specs.py` script. Issues are likely related to SSH connectivity or permissions on the remote machine for the script to run (Polaris handles script execution).

(General troubleshooting for "Invoke-WebRequest not recognized", etc., remains the same as v2.0.0)

## 📞 Support
(Contact methods remain the same)

---

**Ready to manage your mining operations on Windows with improved SSH and auto-detection?** Follow the installation instructions above for v2.0.1! 🚀 