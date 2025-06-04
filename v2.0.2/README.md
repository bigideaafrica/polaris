# Polaris Node Manager v2.0.2

**Enhanced Connection System & Security**

Welcome to Polaris Node Manager v2.0.2 - featuring a completely redesigned connection system with enhanced security, streamlined SSH key management, and improved user experience.

## 🆕 What's New in v2.0.2

### 🔄 **Connection System Improvements**
- **API-Based Architecture**: Completely redesigned connection system using a robust API-based approach for enhanced reliability and security
- **Improved SSH Handling**: More reliable SSH key authentication and connection management
- **Better Error Handling**: Enhanced error messages and troubleshooting feedback for connection issues

### 🔑 **Enhanced Security & Authentication**
- **Simplified SSH Key Setup**: Direct key input via text areas instead of requiring file path specifications
- **Secure Key Processing**: Enhanced private key handling through the updated connection system
- **Flexible Key Input**: Support for both direct paste input and file loading with "Load Key from File" button
- **Better Authentication Flow**: Streamlined authentication process with improved security measures

### 💻 **User Interface Improvements**
- **Streamlined Workflow**: Simplified process for adding and connecting to remote machines
- **Enhanced Key Input**: Intuitive text area for SSH private key input with optional file loading
- **Better Feedback**: Improved connection status updates and clearer error messages
- **Modern Design**: Updated interface elements for better user experience

### 🚀 **Performance & Reliability**
- **Robust Connections**: Enhanced connection stability and error handling
- **Consistent Experience**: Unified connection method across all remote machine operations
- **Better Integration**: Improved integration with existing API infrastructure
- **Backward Compatibility**: Maintains full compatibility with existing setups

## Key Features (v2.0.0 + v2.0.1 + v2.0.2)

### Multi-Machine Management
- **Unified UID System**: Manage multiple mining rigs under a single unique identifier
- **Centralized Control**: Monitor and control all connected machines from one interface
- **Scalable Architecture**: Support for growing mining operations

### Advanced Security & Connection
- **API-Based Connections**: Modern, secure connection management (v2.0.2)
- **Simplified SSH Setup**: Direct key input with optional file loading (v2.0.2)
- **OpenSSH Integration**: Direct OpenSSH calls for improved stability (v2.0.1)
- **Secure Authentication**: Enhanced private key handling and authentication

### Automated Detection & Validation
- **Hardware Auto-Detection**: Python-based automatic remote hardware detection (v2.0.1)
- **Self-Validation System**: Automated server authentication and performance benchmarking
- **Resource Management**: Verified compute resource deletion with Firebase API (v2.0.1)

### Real-Time Monitoring
- **Live Status Tracking**: Real-time monitoring of all connected mining machines
- **Activity Logging**: Comprehensive logging of mining operations and system events
- **Performance Metrics**: CPU/GPU scoring and resource utilization monitoring
- **Network Monitoring**: Connection health and response time tracking

### Modern Interface
- **React-Based UI**: Clean, responsive interface built with React and Material-UI Joy
- **Streamlined Design**: Improved workflow and user experience (v2.0.2)
- **Cross-Platform**: Optimized for Windows, macOS, and Linux

## System Requirements

### Minimum Requirements
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 500MB disk space
- **Network**: Stable internet connection for API-based connections
- **Permissions**: Administrator/sudo privileges for installation

### New Dependencies (v2.0.2)
- **OpenSSH Client**: For secure machine connections
- **Python 3.x**: For hardware detection and connection management
- **Modern Web Browser**: For enhanced UI components (Chromium-based recommended)

### Platform-Specific Requirements

#### Windows
- Windows 10 or later (64-bit)
- OpenSSH Client (Windows 10 1809+ includes built-in client)
- .NET Framework 4.8+ (included in installer)
- Windows PowerShell 5.0+

#### Linux
- Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, Debian 11+)
- OpenSSH client package (`openssh-client`)
- systemd support (for service management)
- GTK3+ libraries (for GUI)
- Python 3.6+ with pip

#### MacOS
- macOS 10.15 (Catalina) or later
- OpenSSH (pre-installed on macOS)
- Apple Silicon (M1/M2) and Intel processors supported
- Python 3.6+ (can be installed via Homebrew)

## Download & Installation

### Quick Start

1. **Download**: Visit [Releases](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.2) page
2. **Choose Your Platform**: 
   - Windows: `polaris-node-manager-windows.zip` (174 MB)
   - Linux: `polaris-node-manager-linux.zip` (402 MB)
   - macOS: `polaris-node-manager-macos.zip` (891 MB)
3. **Install**: Follow platform-specific instructions below

### Platform-Specific Installation

#### Windows Installation
```cmd
:: Download using curl
curl -L -o polaris-v2.0.2-windows.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-windows.zip

:: Extract (requires tar on Windows 10+)
tar -xf polaris-v2.0.2-windows.zip

:: Run installer
cd polaris-node-manager-windows
polaris-node-manager-setup.exe
```

**PowerShell Alternative:**
```powerShell
# Download
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-windows.zip" -OutFile "polaris-v2.0.2-windows.zip"

# Extract
Expand-Archive -Path "polaris-v2.0.2-windows.zip" -DestinationPath "polaris-v2.0.2-windows"

# Run installer
Set-Location "polaris-v2.0.2-windows"
.\polaris-node-manager-setup.exe
```

#### Linux Installation
```bash
# Download
wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-linux.zip

# Extract
unzip polaris-node-manager-linux.zip

# Make executable and install
cd polaris-node-manager-linux
chmod +x polaris-node-manager.AppImage
sudo mv polaris-node-manager.AppImage /usr/local/bin/polaris-node-manager

# Create desktop entry (optional)
./create-desktop-entry.sh
```

#### macOS Installation
```bash
# Download
curl -L -o polaris-v2.0.2-macos.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-macos.zip

# Extract
unzip polaris-v2.0.2-macos.zip

# Install
cd polaris-node-manager-macos
sudo installer -pkg polaris-node-manager.pkg -target /
```

## Using v2.0.2 Features

### Setting Up SSH Connections (New in v2.0.2)

1. **Add New Machine**:
   - Click "Add Machine" in the main interface
   - Enter machine details (IP, username, etc.)

2. **SSH Key Setup** (Choose one method):
   
   **Method 1: Direct Key Input (Recommended)**
   - Paste your SSH private key directly into the "SSH Private Key" text area
   - The system will validate and process the key securely
   
   **Method 2: Load from File**
   - Click "Load Key from File" button
   - Select your private key file (.pem, .key, or id_rsa)
   - The key content will be loaded automatically

3. **Connect**:
   - Click "Connect" to establish the connection
   - The new API-based system will handle authentication
   - Monitor connection status in real-time

### Enhanced Security Features

- **Secure Key Storage**: Private keys are processed securely without permanent storage
- **Connection Validation**: Automatic validation of SSH credentials before connection
- **Error Recovery**: Improved error handling with suggested fixes
- **Session Management**: Better handling of connection sessions and timeouts

## Troubleshooting

### Connection Issues
- **Problem**: SSH connection fails
- **Solution**: Verify SSH key format and ensure OpenSSH client is installed

### Key Loading Issues
- **Problem**: Cannot load SSH key from file
- **Solution**: Ensure key file has proper permissions (600) and correct format

### API Connection Issues
- **Problem**: API-based connection fails
- **Solution**: Check internet connectivity and firewall settings

## Migration from v2.0.1

v2.0.2 is fully backward compatible with v2.0.1. Your existing configurations will work seamlessly with the new connection system. The enhanced SSH key management is optional - you can continue using file-based keys if preferred.

### What Changes
- Connection reliability improves automatically
- New SSH key input options become available
- Better error messages and feedback

### What Stays the Same
- All existing machine configurations
- Mining operation settings
- Performance monitoring data
- User interface layout (with enhancements)

## Support & Resources

- **Documentation**: [Platform-specific guides](../README.md#available-versions)
- **Issues**: [GitHub Issues](https://github.com/bigideaafrica/polaris_distributions/issues)
- **Contact Support**: Use the in-app support feature with machine-specific problem reporting

## Version History

- **v2.0.2** (Current) - Enhanced connection system and security
- **v2.0.1** - SSH overhaul and automated hardware detection
- **v2.0.0** - Multi-machine management and self-validation
- **v1.0.0** - Legacy single-machine setup

---

**Ready to upgrade?** Download v2.0.2 and experience the enhanced connection system with improved security and streamlined user experience. 