# Polaris Node Manager v2.0.2 - Windows Installation Guide

**Enhanced Connection System & Security for Windows**

This guide covers the installation and usage of Polaris Node Manager v2.0.2 on Windows systems, featuring the new API-based connection system and enhanced SSH key management.

## 🆕 Windows-Specific v2.0.2 Features

### Enhanced Windows Integration
- **Native OpenSSH Support**: Utilizes Windows 10/11 built-in OpenSSH client for better compatibility
- **PowerShell & Command Prompt Support**: Complete installation instructions for both shells
- **Windows Defender Integration**: Optimized to work seamlessly with Windows security features
- **Modern File Dialog**: Enhanced file selection for SSH key loading with Windows Explorer integration

### Improved Windows Performance
- **API-Based Connections**: Reduced dependency on traditional SSH libraries for better Windows compatibility
- **Background Processing**: Enhanced background task handling for Windows services
- **Memory Management**: Improved memory usage on Windows systems
- **Startup Optimization**: Faster application startup and connection establishment

## System Requirements

### Minimum Requirements
- **OS**: Windows 10 (version 1809) or Windows 11
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 500MB free disk space
- **Network**: Stable internet connection for API-based connections
- **Permissions**: Administrator privileges for installation

### Required Components
- **OpenSSH Client**: Windows 10 1809+ includes built-in client (automatically available)
- **.NET Framework**: 4.8 or later (included in installer)
- **Visual C++ Redistributable**: 2019 or later (included in installer)
- **Windows PowerShell**: 5.0+ (pre-installed on Windows 10/11)

### Optional Components
- **Python 3.x**: For advanced hardware detection features (can be installed automatically)
- **Git**: For repository access (optional, can be installed via installer)

## Download & Installation

### Method 1: Quick Download (Recommended)

**Download the latest Windows build:**
- **File**: `polaris-node-manager-windows.zip`
- **Size**: 174 MB
- **URL**: [GitHub Releases v2.0.2](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.2)

### Method 2: Command Line Download

**Using Command Prompt:**
```cmd
:: Create download directory
mkdir %USERPROFILE%\Downloads\polaris-v2.0.2
cd %USERPROFILE%\Downloads\polaris-v2.0.2

:: Download using curl (available on Windows 10+)
curl -L -o polaris-v2.0.2-windows.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-windows.zip

:: Extract using tar (available on Windows 10+)
tar -xf polaris-v2.0.2-windows.zip

:: Navigate to extracted folder
cd polaris-node-manager-windows
```

**Using PowerShell:**
```powershell
# Create download directory
New-Item -ItemType Directory -Path "$env:USERPROFILE\Downloads\polaris-v2.0.2" -Force
Set-Location "$env:USERPROFILE\Downloads\polaris-v2.0.2"

# Download
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-windows.zip" -OutFile "polaris-v2.0.2-windows.zip"

# Extract
Expand-Archive -Path "polaris-v2.0.2-windows.zip" -DestinationPath "polaris-v2.0.2-windows" -Force

# Navigate to extracted folder
Set-Location "polaris-v2.0.2-windows"
```

## Installation Process

### Standard Installation (Recommended)

1. **Run the Installer:**
   ```cmd
   :: Double-click or run from command line
   polaris-node-manager-setup.exe
   ```

2. **Follow Installation Wizard:**
   - Accept the license agreement
   - Choose installation directory (default: `C:\Program Files\Polaris Node Manager`)
   - Select components (all recommended for v2.0.2 features)
   - Allow administrator elevation when prompted

3. **Post-Installation:**
   - Application will be added to Start Menu
   - Desktop shortcut created (optional)
   - Windows Firewall exception added automatically

### Portable Installation

For users who prefer not to install system-wide:

1. **Extract to Desired Location:**
   ```cmd
   :: Extract to a folder like C:\Tools\PolarisNodeManager
   tar -xf polaris-node-manager-windows.zip -C C:\Tools\
   ```

2. **Run Directly:**
   ```cmd
   cd C:\Tools\polaris-node-manager-windows
   polaris-node-manager.exe
   ```

## Using v2.0.2 Features on Windows

### Setting Up SSH Connections

#### Method 1: Direct Key Input (New in v2.0.2)

1. **Launch Application:**
   - Start Menu → "Polaris Node Manager"
   - Or run from installation directory

2. **Add New Machine:**
   - Click "Add Machine" button
   - Enter machine details:
     - **Hostname/IP**: Target machine address
     - **Username**: SSH username
     - **Port**: SSH port (default: 22)

3. **SSH Key Setup:**
   - **Option A - Direct Paste** (Recommended):
     - Copy your SSH private key content
     - Paste directly into "SSH Private Key" text area
     - System validates key format automatically
   
   - **Option B - Load from File**:
     - Click "Load Key from File" button
     - Use Windows Explorer to select key file (.pem, .key, id_rsa)
     - Common locations: `%USERPROFILE%\.ssh\`, `C:\Users\YourName\.ssh\`

4. **Connect:**
   - Click "Connect" button
   - Monitor connection status in real-time
   - Enhanced error messages guide troubleshooting

#### SSH Key Locations on Windows

**Common SSH key locations:**
```cmd
:: User SSH directory
%USERPROFILE%\.ssh\
:: Examples:
:: C:\Users\YourName\.ssh\id_rsa
:: C:\Users\YourName\.ssh\id_ed25519
:: C:\Users\YourName\.ssh\my-server.pem
```

**Generating SSH Keys on Windows:**
```cmd
:: Using built-in OpenSSH
ssh-keygen -t ed25519 -C "your-email@example.com"
:: Or RSA format
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```

### Enhanced Windows Features

#### Windows Firewall Configuration
The installer automatically configures Windows Firewall, but manual configuration may be needed:

```powershell
# Allow Polaris through Windows Firewall (Run as Administrator)
New-NetFirewallRule -DisplayName "Polaris Node Manager" -Direction Inbound -Protocol TCP -LocalPort 8080 -Action Allow
```

#### Windows Service Integration
v2.0.2 includes improved Windows service integration:

- **Background Operation**: Application can run minimized to system tray
- **Startup Options**: Configure to start with Windows
- **Service Management**: Better integration with Windows service architecture

### Windows-Specific Troubleshooting

#### OpenSSH Client Issues

**Problem**: SSH connections fail with "ssh: command not found"
**Solution**: Ensure OpenSSH Client is enabled

```powershell
# Check if OpenSSH Client is installed (Run as Administrator)
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH.Client*'

# Install if missing
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

#### PowerShell Execution Policy

**Problem**: PowerShell scripts blocked by execution policy
**Solution**: Temporarily adjust execution policy

```powershell
# Check current policy
Get-ExecutionPolicy

# Set to RemoteSigned (Run as Administrator)
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

#### Windows Defender Issues

**Problem**: Windows Defender flags application
**Solution**: Add exclusion for Polaris Node Manager

```powershell
# Add folder exclusion (Run as Administrator)
Add-MpPreference -ExclusionPath "C:\Program Files\Polaris Node Manager"
```

#### Permission Issues

**Problem**: Cannot write to application directory
**Solution**: Ensure proper permissions

```cmd
:: Run installer as Administrator
:: Or adjust folder permissions
icacls "C:\Program Files\Polaris Node Manager" /grant %USERNAME%:F
```

#### Connection Timeout Issues

**Problem**: API-based connections timeout
**Solution**: Check Windows Firewall and network settings

```powershell
# Test network connectivity
Test-NetConnection -ComputerName your-target-server -Port 22

# Check Windows Firewall rules
Get-NetFirewallRule -DisplayName "*Polaris*"
```

### Windows Performance Optimization

#### For Better Performance

1. **Disable Windows Search Indexing** for Polaris directory:
   ```cmd
   :: Exclude from indexing
   attrib +I "C:\Program Files\Polaris Node Manager"
   ```

2. **Configure Windows Power Settings**:
   - Set power plan to "High Performance" for mining operations
   - Disable "USB selective suspend"

3. **Network Optimization**:
   ```cmd
   :: Optimize network settings for mining
   netsh int tcp set global autotuninglevel=normal
   ```

## Advanced Windows Configuration

### Environment Variables

Set environment variables for easier CLI access:

```cmd
:: Add to PATH
setx PATH "%PATH%;C:\Program Files\Polaris Node Manager"

:: Set Python path if using auto-detection
setx POLARIS_PYTHON_PATH "C:\Python39\python.exe"
```

### Registry Configuration

Advanced users can configure registry settings:

```reg
:: Example registry entries (use with caution)
[HKEY_CURRENT_USER\Software\PolarisNodeManager]
"AutoStart"=dword:00000001
"MinimizeToTray"=dword:00000001
```

## Uninstallation

### Standard Uninstall
1. **Control Panel Method:**
   - Control Panel → Programs and Features
   - Select "Polaris Node Manager v2.0.2"
   - Click "Uninstall"

2. **Settings Method (Windows 10/11):**
   - Settings → Apps → Apps & features
   - Find "Polaris Node Manager"
   - Click "Uninstall"

### Complete Removal
```cmd
:: Remove user data (optional)
rmdir /s "%APPDATA%\PolarisNodeManager"
rmdir /s "%LOCALAPPDATA%\PolarisNodeManager"

:: Remove SSH keys if desired
:: rmdir /s "%USERPROFILE%\.ssh"
```

## Migration from v2.0.1

v2.0.2 automatically migrates your existing configuration:

1. **Backup Creation**: Previous settings backed up to `%APPDATA%\PolarisNodeManager\backup\`
2. **Configuration Migration**: SSH keys and machine configurations preserved
3. **New Features**: Enhanced connection system activated automatically

**Manual Migration (if needed):**
```cmd
:: Copy old configuration
copy "%APPDATA%\PolarisNodeManager\v2.0.1\config.json" "%APPDATA%\PolarisNodeManager\v2.0.2\"
```

## Support Resources

### Windows-Specific Support
- **Event Viewer**: Check Windows Event Viewer for application logs
- **Performance Monitor**: Monitor resource usage during mining operations
- **Task Manager**: Monitor Polaris processes and resource consumption

### Getting Help
- **In-App Support**: Use Contact Support feature with machine selection
- **Log Files**: Located at `%APPDATA%\PolarisNodeManager\logs\`
- **GitHub Issues**: [Report Windows-specific issues](https://github.com/bigideaafrica/polaris_distributions/issues)

### Useful Windows Commands
```cmd
:: Check system information
systeminfo | findstr /B /C:"OS Name" /C:"OS Version"

:: Check network configuration
ipconfig /all

:: Check installed .NET versions
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP" /s

:: View application logs
eventvwr.msc
```

---

**Windows Installation Complete!** You're now ready to use Polaris Node Manager v2.0.2 with the enhanced connection system and improved Windows integration. 