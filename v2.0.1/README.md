# Polaris Node Manager v2.0.1

Welcome to **Polaris Node Manager v2.0.1**! This version focuses on significant backend improvements for SSH stability, introduces automated hardware detection, and ensures alignment with our resource management APIs.

## 🌟 Overview

Polaris Node Manager v2.0.1 builds upon the robust multi-machine management features of v2.0.0, enhancing core functionalities for a more reliable and efficient user experience. Key updates include an SSH client overhaul and a new Python-based script for automatic remote hardware specification detection.

## 🆕 What's New in v2.0.1

- **SSH Client Overhaul**:
  - Replaced the `electron-ssh2` library with direct **OpenSSH calls**.
  - This change significantly improves SSH connection stability, security, and compatibility.
- **Automated Remote Hardware Detection**:
  - Integrated `detect_compute_specs.py`, a new Python-based script for automatic detection of remote machine hardware (CPU, GPU, RAM, Storage).
  - Replaces previous manual methods, streamlining the machine addition process.
  - The SSH connection flow has been updated to utilize this new Python-based detection script.
- **Compute Resource Deletion Verified**:
  - Confirmed that the existing compute resource deletion functionality aligns correctly with the Firebase API, ensuring proper resource management.

## ✨ Key Features (from v2.0.0, enhanced in v2.0.1)

### 🔧 Multi-Machine Management
- **Unified UID System**: Register and manage multiple mining rigs under a single user identifier.
- **Centralized Control**: Monitor and control all your mining machines from one interface.
- **Scalable Architecture**: Add unlimited mining machines to your network.
- **Machine Table View**: Comprehensive view of all mining rigs with specifications, IP addresses, ports, and status.
- **Bulk Operations**: Refresh all machines or stop all operations with single-click actions.

### 🌐 Bittensor Network Integration
- **Subnet Registration**: Seamless integration with Bittensor subnet 49 (polariscloud.ai).
- **UID Management**: Automatic UID assignment and tracking.
- **Network Status**: Real-time subnet registration status and connectivity monitoring.
- **Wallet Integration**: Register and manage cryptocurrency wallets for mining operations.

### 🛡️ Advanced Validation System
- **Automated Server Authentication**: Now more robust with direct OpenSSH calls and Python-based hardware detection.
- **Performance Benchmarking**: Built-in CPU and GPU performance scoring.
- **System Verification**: Comprehensive hardware detection (now automated via `detect_compute_specs.py`).
- **Proof of Work**: Real-time system benchmarking with performance scoring.

### 📊 Real-Time Monitoring & Logging
- **Live Status Tracking**: Monitor all connected mining machines in real-time.
- **Activity Logging**: Detailed logging of mining operations, system events, and SSH interactions.
- **API Response Monitoring**: Track all API communications and server responses.
- **Performance Metrics**: Track CPU scores, GPU scores, and total performance ratings.
- **Network Monitoring**: Monitor connection status and response times.
- **Session Management**: Track session expiration and user authentication status.

### 🎛️ Machine Management Interface
- **Detailed Machine Specs**: View automatically detected CPU/GPU information, RAM, storage, and IP configurations.
- **Status Indicators**: Real-time status updates (Connected, Pending, Rejected).
- **Validation Status**: Track verification status for each machine.
- **Individual Actions**: Configure, delete, or manage individual machines (deletion now fully verified with Firebase API).
- **Search & Filter**: Search by miner username and filter by status.

### 🎨 Modern User Interface
- **React + Material-UI Joy**: Clean, responsive, and intuitive interface.
- **Cross-Platform Design**: Consistent experience across Windows, macOS, and Linux.
- **Real-Time Updates**: Live status indicators and progress tracking.
- **Responsive Layout**: Optimized for different screen sizes and resolutions.
- **Session Indicators**: User welcome messages and session expiration timers.

### 🛠️ Support & Maintenance
- **Contact Support System**: Advanced built-in support contact system.
  - Machine-Specific Support, Multi-Query Support, Issue Descriptions, Screenshot Attachments, Alternative Channels, Real-time Submission.
- **Activity Logs**: Exportable logs for troubleshooting.
- **Clear Logs**: Easy log management.
- **User Management**: User session tracking and logout.

### 🖥️ Enhanced Cross-Platform Support
- **Windows**: Universal ZIP build and traditional installer.
- **Linux**: Universal ZIP build (containing AppImage) and direct AppImage.
- **MacOS**: Universal ZIP build and traditional DMG installer.

## 📥 Downloads (v2.0.1)

Choose the appropriate installer for your operating system. **Please ensure you download the v2.0.1 packages.**

### Windows
- [**Windows Build (v2.0.1)**](./windows/polaris-node-manager-windows-v2.0.1.zip) - Universal Windows application (~175MB expected)
- [Windows Installer (v2.0.1)](./windows/PolarisNodeManagerSetup-v2.0.1.exe) - Traditional installer (~75MB expected)

### Linux
- [**Linux Build (v2.0.1)**](./linux/polaris-node-manager-linux-v2.0.1.zip) - Universal Linux application (~405MB expected)
- [AppImage (x64, v2.0.1)](./linux/PolarisNodeManager-v2.0.1.AppImage) - Alternative AppImage format (~100MB expected)

### MacOS
- [**macOS Build (v2.0.1)**](./macos/polaris-node-manager-macos-v2.0.1.zip) - Universal macOS application (~895MB expected)
- [DMG Installer (v2.0.1)](./macos/PolarisNodeManager-v2.0.1.dmg) - Traditional DMG installer (~95MB expected)

*Note: Exact file sizes for v2.0.1 are estimates and will be confirmed upon release.*

## 🚀 Quick Start (v2.0.1)

### 1. Installation

> **💡 Windows Users**: If you get an error like "'Invoke-WebRequest' is not recognized", you're using **Command Prompt** instead of **PowerShell**. Use Option A below for Command Prompt, or open PowerShell for Option B.

#### Windows

**Option A: Command Prompt (cmd.exe) for v2.0.1 ZIP**
```cmd
REM Download Windows build v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/polaris-node-manager-windows-v2.0.1.zip" -o "polaris-node-manager-windows-v2.0.1.zip"

REM Extract using built-in tar
tar -xf polaris-node-manager-windows-v2.0.1.zip -C polaris-node-manager-v2.0.1

REM Navigate and run
cd polaris-node-manager-v2.0.1
polaris-node-manager.exe
```

**Option B: PowerShell for v2.0.1 ZIP**
```powershell
# Download Windows build v2.0.1
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/windows/polaris-node-manager-windows-v2.0.1.zip" -OutFile "polaris-node-manager-windows-v2.0.1.zip"

# Extract the ZIP file
Expand-Archive -Path "polaris-node-manager-windows-v2.0.1.zip" -DestinationPath ".\polaris-node-manager-v2.0.1"

# Run the application
cd polaris-node-manager-v2.0.1
.\polaris-node-manager.exe
```

#### Linux (v2.0.1 ZIP with AppImage)
```bash
# Download Linux build v2.0.1
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/linux/polaris-node-manager-linux-v2.0.1.zip"

# Extract the file
unzip polaris-node-manager-linux-v2.0.1.zip -d polaris-node-manager-v2.0.1
cd polaris-node-manager-v2.0.1

# Make executable and run
chmod +x ./polaris-node-manager.AppImage # Or specific AppImage name if different
./polaris-node-manager.AppImage
```

#### MacOS (v2.0.1 ZIP)
```bash
# Download macOS build v2.0.1
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2.0.1/macos/polaris-node-manager-macos-v2.0.1.zip" -o "polaris-node-manager-macos-v2.0.1.zip"

# Extract the file
unzip polaris-node-manager-macos-v2.0.1.zip -d polaris-node-manager-v2.0.1
cd polaris-node-manager-v2.0.1

# Open extracted folder and double-click the app
open "Polaris Node Manager.app" # Or specific .app name if different
```

### 2. Adding Your First Mining Machine
The process remains similar to v2.0.0, but benefits from the new automated hardware detection:
1. **Launch** Polaris Node Manager v2.0.1.
2. **Click** "Add Mining Machine".
3. **Follow** the automated setup process:
   - **Connect**: Enter machine connection details. The improved SSH client handles this more reliably.
   - **System**: Hardware specifications (CPU, GPU, RAM, Storage) are now automatically detected using `detect_compute_specs.py`.
   - **Validation**: Automated server authentication and performance testing.
   - **Register**: Complete machine registration under your UID.

### 3. Validation Process
The validation system is enhanced by the SSH and hardware detection improvements:
- **Server Authentication**: More reliable SSH access verification.
- **Proof of Work**: CPU/GPU benchmarking on automatically detected hardware.

## ⚠️ Important Notes
(Same as v2.0.0)
Before installing Polaris Node Manager v2.0.1, please ensure:
- **System Requirements**: Ensure your system meets minimum requirements.
- **Stable Internet Connection**: For mining and real-time monitoring.
- **Admin Privileges**: May be required for setup.
- **Keep App Updated**: Check for future updates.

## 📋 System Requirements
(Largely unchanged from v2.0.0, ensure sufficient space for potentially slightly larger builds due to new scripts/dependencies if any)

### Minimum Requirements
- **RAM**: 4GB (8GB recommended for managing 5+ machines).
- **Storage**: 500MB-1GB free disk space (plus space for ZIP extraction, e.g., up to ~900MB for macOS ZIP).
- **Network**: Stable internet connection (minimum 10 Mbps).
- **CPU**: Dual-core processor (Quad-core recommended).

### Recommended for Optimal Performance
- **RAM**: 16GB+ for managing 10+ mining machines.
- **Storage**: 2GB+ free disk space (for logs and cache).
- **Network**: High-speed connection (100+ Mbps).
- **CPU**: Multi-core processor (6+ cores).

### Platform-Specific Requirements

#### Windows
- Windows 10 or later (64-bit).
- 1GB free disk space (for ZIP build extraction).
- .NET Framework (included in builds).
- **OpenSSH Client**: For the new SSH overhaul, ensure the Windows OpenSSH client feature is enabled (usually on by default in modern Windows 10/11).

#### Linux
- Modern Linux distribution with desktop environment.
- 1GB free disk space (for ZIP build extraction).
- **Python 3.x**: Required for `detect_compute_specs.py`. Ensure it's installed and in PATH.
- **OpenSSH Client**: Must be installed and accessible.

#### MacOS
- macOS 10.15 (Catalina) or later.
- 2GB free disk space (for ZIP build extraction).
- Universal binary supports both Apple Silicon and Intel Macs.
- **Python 3.x**: Ensure it's available (usually pre-installed or easily installable via Homebrew).
- **OpenSSH Client**: Included with macOS.

## 🔧 Features Deep Dive
(Largely the same as v2.0.0, with enhancements as noted in "What's New")
... (Sections on Multi-Machine Management, Self-Validation System, Real-Time Monitoring can be briefly reviewed for any direct impact from v2.0.1 changes, e.g., "Self-Validation System now leverages automated hardware detection") ...

## 🆕 What's Changed from v2.0.0 to v2.0.1

| Feature Area        | Change in v2.0.1                                                                 | Impact                                                                 |
|---------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------|
| **SSH Connectivity** | Replaced `electron-ssh2` with direct OpenSSH calls.                             | Improved stability, security, and compatibility with SSH servers.      |
| **Hardware Detection**| Integrated `detect_compute_specs.py` (Python script).                           | Automated CPU, GPU, RAM, Storage detection; replaces manual methods.   |
| **Connection Flow** | Updated to use Python-based hardware detection during SSH connection.            | Streamlined machine setup; more accurate initial spec reporting.       |
| **Resource Deletion**| Verified compute resource deletion endpoint functionality with Firebase API.        | Confirmed backend alignment; ensures reliable resource management.     |
| **Dependencies**    | Potential new dependency on Python 3.x for remote hardware detection script.      | Users may need Python 3.x on their system for full functionality.      |

## 🛠️ Advanced Configuration
(Same as v2.0.0)
### Environment Variables
...
### Configuration Files
...

## 🐛 Troubleshooting (v2.0.1)

### Common Issues
- **SSH Connection Failures**:
    - Ensure OpenSSH client is installed and working on the system running Polaris Node Manager.
    - Verify remote machine's SSH server is configured correctly.
    - Check firewall settings on both local and remote machines.
- **Hardware Detection Issues**:
    - Ensure Python 3.x is installed and in the system's PATH if `detect_compute_specs.py` fails.
    - The Python script needs permissions to execute and gather hardware info on the remote machine (handled via SSH).
- **"Invoke-WebRequest not recognized"**: (Same as v2.0.0) Use Command Prompt (curl) or ensure you are in PowerShell.

### Support
(Same as v2.0.0)
...

## 📈 Performance Optimization
(Same as v2.0.0, though SSH changes might offer slight performance benefits in connection times)
...

## 🔄 Migration from v2.0.0 to v2.0.1
- No specific migration steps are typically needed for minor patch versions like this.
- Simply download and install v2.0.1. Existing configurations should be compatible.
- If new dependencies like Python are required for full functionality (hardware detection), ensure they are met.

## 📊 Version History

### v2.0.1 (Current Release)
- ✅ SSH client overhaul (direct OpenSSH calls).
- ✅ Automated remote hardware detection (`detect_compute_specs.py`).
- ✅ Updated SSH connection flow with Python-based detection.
- ✅ Verified compute resource deletion with Firebase API.

### v2.0.0
- ✅ Multi-machine management with unified UID
- ✅ Automated self-validation system
- ✅ Modern React + Material-UI interface
- ✅ Real-time monitoring and activity logging
- ✅ Enhanced cross-platform support (Windows/Linux/MacOS)
- ✅ Performance benchmarking and scoring
- ✅ Advanced SSH authentication and connectivity testing

### Coming Soon (Post v2.0.1)
- 📊 Advanced analytics dashboard
- 📈 Historical performance tracking
- 🔔 Advanced notification system
- 🌐 Web-based remote management
- 📱 Mobile companion app

## 📄 License
(Same as v2.0.0)
Polaris Node Manager v2.0.1 is distributed under the [MIT License](https://opensource.org/licenses/MIT).

---

**Ready to manage your mining empire with enhanced stability and automation?** Download Polaris Node Manager v2.0.1 today! 🚀 