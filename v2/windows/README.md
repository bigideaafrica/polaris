# Polaris Node Manager v2.0.0 - Windows

Welcome to the Windows distribution of **Polaris Node Manager v2**! This package contains optimized Windows installers and portable versions for managing your mining operations.

## 📦 Available Downloads

### Windows Build (Recommended)
- **polaris-node-manager-windows.zip** - Universal Windows application bundle
- **File Size**: ~174 MB (174,000 KB)
- **Installation**: Extract ZIP and run
- **Updates**: Manual download required
- **Compatibility**: Works on all Windows 10+ systems

### Windows Installer (Alternative)
- **Polaris Node Manager Setup 0.17.1.exe** - Traditional Windows installer with shortcuts and auto-updates
- **File Size**: ~73MB (72,776 KB)
- **Installation**: Automatic with Windows integration
- **Updates**: Built-in update system

## 🔧 System Requirements

### Minimum Requirements
- **OS**: Windows 10 (build 1903) or Windows 11
- **Architecture**: 64-bit (x86_64)
- **RAM**: 4GB minimum (8GB recommended)
- **Storage**: 500MB free disk space
- **Network**: Internet connection required
- **Permissions**: Administrator privileges for installer

### Recommended Configuration
- **OS**: Windows 11 (latest updates)
- **RAM**: 8GB+ for managing multiple machines
- **Storage**: 2GB+ free space (for logs and cache)
- **Network**: High-speed connection (50+ Mbps)
- **Antivirus**: Windows Defender exclusion recommended

## 🚀 Installation Instructions

> **💡 Which Command Interface Should I Use?**
> 
> - **Command Prompt (cmd.exe)**: The black window that opens by default when you search "cmd" or "Command Prompt"
> - **PowerShell**: The blue window when you search "PowerShell" in Start Menu
> - **How to Open**:
>   - **Command Prompt**: Press `Windows + R`, type `cmd`, press Enter
>   - **PowerShell**: Press `Windows + R`, type `powershell`, press Enter
>   - **Or**: Search "Command Prompt" or "PowerShell" in Start Menu

### Method 1: ZIP Build (Recommended)

#### Option A: Command Prompt (cmd.exe)
```cmd
REM Download Windows build
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/windows/polaris-node-manager-windows.zip" -o "polaris-node-manager-windows.zip"

REM Extract using built-in tar (Windows 10+)
tar -xf polaris-node-manager-windows.zip

REM Navigate to extracted folder
cd polaris-node-manager

REM Run the application
polaris-node-manager.exe
```

#### Option B: PowerShell
```powershell
# Download Windows build
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/windows/polaris-node-manager-windows.zip" -OutFile "polaris-node-manager-windows.zip"

# Extract the ZIP file
Expand-Archive -Path "polaris-node-manager-windows.zip" -DestinationPath ".\polaris-node-manager"

# Navigate to extracted folder
cd polaris-node-manager

# Run the application
.\polaris-node-manager.exe
```

#### Option C: Manual Download (Easiest)
1. **Go to**: `https://github.com/bigideaafrica/polaris_distributions/tree/main/v2/windows`
2. **Click** on `polaris-node-manager-windows.zip`
3. **Click** "Download" button
4. **Right-click** the downloaded ZIP → "Extract All..."
5. **Navigate** to extracted folder and **double-click** `polaris-node-manager.exe`

### Method 2: Traditional Installer

#### Option A: Command Prompt (cmd.exe)
```cmd
REM Download installer
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/windows/Polaris Node Manager Setup 0.17.1.exe" -o "setup.exe"

REM Run installer (requires admin privileges)
setup.exe
```

#### Option B: PowerShell
```powershell
# Download installer
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/windows/Polaris%20Node%20Manager%20Setup%200.17.1.exe" -OutFile "Polaris Node Manager Setup 0.17.1.exe"

# Run with administrator privileges
Start-Process -FilePath ".\Polaris Node Manager Setup 0.17.1.exe" -Verb RunAs
```

## 📂 File Structure

### ZIP Build Structure
```
polaris-node-manager/
├── polaris-node-manager.exe           # Main application
├── resources/                          # Application resources
├── locales/                           # Language files
├── lib/                               # Required libraries
├── data/                              # User data and configurations
├── logs/                              # Application logs
└── README.txt                         # Quick reference
```

### Installed Version Structure
```
C:\Program Files\PolarisNodeManager\
├── PolarisNodeManager.exe              # Main application
├── resources\                           # Application resources
├── locales\                            # Language files
├── uninstall.exe                       # Uninstaller
└── README.txt                         # Quick reference
```

## 🏃‍♂️ Running the Application

### First Launch
1. **Launch** Polaris Node Manager v2
2. **Accept** any Windows security prompts
3. **Complete** the initial setup wizard:
   - Create or import user account
   - Configure network settings
   - Set up Bittensor wallet (if needed)

### Adding Mining Machines
1. **Click** "Add Machine" button
2. **Enter** connection details:
   - Machine IP address
   - SSH credentials
   - Custom port (if different from 22)
3. **Follow** the automated validation process
4. **Review** machine specifications and performance scores

## 🛠️ Configuration

### Application Settings
- **Location**: `%APPDATA%\PolarisNodeManager\config.json`
- **Logs**: `%APPDATA%\PolarisNodeManager\logs\`
- **Cache**: `%APPDATA%\PolarisNodeManager\cache\`

### Environment Variables
```powershell
# Set custom configuration directory
$env:POLARIS_CONFIG_DIR = "C:\Custom\Config\Path"

# Enable debug logging
$env:POLARIS_DEBUG = "true"

# Set custom log level
$env:POLARIS_LOG_LEVEL = "debug"
```

### Windows Defender Configuration
Add exclusions for better performance:
```powershell
# Add application folder to exclusions
Add-MpPreference -ExclusionPath "C:\Program Files\PolarisNodeManager"

# Add user data folder to exclusions
Add-MpPreference -ExclusionPath "$env:APPDATA\PolarisNodeManager"
```

## 🔥 Windows Firewall

### Automatic Configuration
The installer automatically configures Windows Firewall rules for:
- **Outbound**: HTTPS (443) for API communications
- **Outbound**: SSH (22) for machine connections
- **Outbound**: Custom ports for mining operations

### Manual Firewall Rules
If needed, manually add firewall rules:
```powershell
# Allow outbound HTTPS
New-NetFirewallRule -DisplayName "Polaris HTTPS" -Direction Outbound -Protocol TCP -RemotePort 443

# Allow outbound SSH
New-NetFirewallRule -DisplayName "Polaris SSH" -Direction Outbound -Protocol TCP -RemotePort 22
```

## 🧹 Maintenance

### Clearing Logs
```powershell
# Clear application logs
Remove-Item "$env:APPDATA\PolarisNodeManager\logs\*" -Force

# Clear cache
Remove-Item "$env:APPDATA\PolarisNodeManager\cache\*" -Recurse -Force
```

### Updating the Application
- **Installed Version**: Updates automatically or check "Help > Check for Updates"
- **Portable Version**: Download new version and replace files

### Backup Configuration
```powershell
# Backup user configuration
Copy-Item "$env:APPDATA\PolarisNodeManager" -Destination "C:\Backup\PolarisNodeManager" -Recurse
```

## 🚨 Troubleshooting

### Common Issues

#### "'Invoke-WebRequest' is not recognized" Error
This means you're using **Command Prompt** instead of **PowerShell**:
- **Solution 1**: Use the Command Prompt commands (Option A) instead
- **Solution 2**: Open PowerShell instead:
  - Press `Windows + R`, type `powershell`, press Enter
  - Or search "PowerShell" in Start Menu

#### Application Won't Start
```powershell
# Check if .NET 6.0 is installed
dotnet --version

# Reinstall .NET 6.0 if needed
winget install Microsoft.DotNet.Runtime.6
```

#### Network Connection Issues
- **Check** Windows Firewall settings
- **Verify** internet connectivity
- **Test** SSH access to mining machines manually

#### Performance Issues
- **Close** unnecessary applications
- **Increase** virtual memory if needed
- **Update** graphics drivers
- **Run** disk cleanup

#### Permission Issues
```powershell
# Run as administrator
Start-Process -FilePath "PolarisNodeManager.exe" -Verb RunAs

# Check folder permissions
icacls "$env:APPDATA\PolarisNodeManager" /grant Users:F
```

## 🔄 Uninstallation

### Installed Version
1. **Open** "Add or Remove Programs" in Windows Settings
2. **Find** "Polaris Node Manager v2"
3. **Click** "Uninstall" and follow prompts

### Portable Version
1. **Close** the application
2. **Delete** the PolarisNodeManager folder
3. **Clean** up user data (optional):
   ```powershell
   Remove-Item "$env:APPDATA\PolarisNodeManager" -Recurse -Force
   ```

## 📞 Support

### Windows-Specific Support
- **Event Viewer**: Check Windows Event Viewer for application errors
- **Compatibility**: Use Windows 10/11 compatibility mode if needed
- **Performance**: Use Task Manager to monitor resource usage

### Getting Help
- 📧 **Email**: support@polarisnode.com
- 💬 **Discord**: [Join our community](https://discord.gg/polaris)
- 📖 **Documentation**: [Full docs](https://docs.polarisnode.com)
- 🐛 **Issues**: [GitHub Issues](https://github.com/bigideaafrica/polaris_distributions/issues)

## 📋 Command Line Usage

### Advanced Users
```cmd
# Run with custom configuration
PolarisNodeManager.exe --config="C:\Custom\config.json"

# Run with debug logging
PolarisNodeManager.exe --debug

# Run with specific log level
PolarisNodeManager.exe --log-level=verbose

# Display help
PolarisNodeManager.exe --help
```

### 🛠️ Advanced Support Features

#### Built-in Contact Support System
Polaris Node Manager v2 includes a comprehensive support system:

1. **Access Support**: Click the "Contact Support" button in the main interface
2. **Select Machine**: Choose specific machines from the dropdown list (shows machine ID, username, and status)
3. **Describe Issues**: Use the detailed text area to describe problems with each machine
4. **Multiple Queries**: Add multiple support queries for different machines in one request
5. **Attach Screenshots**: Upload screenshots and images to help illustrate issues
6. **Alternative Channels**: Access direct links to Twitter and Discord for additional support

#### Support Request Features
- **Machine-Specific Support**: Target support requests to specific mining machines
- **Comprehensive Details**: Each machine shows GPU info, IP address, and current status
- **Multi-Machine Support**: Handle multiple machine issues in a single support ticket
- **Visual Evidence**: Attach screenshots and images to support requests
- **Real-time Submission**: Send support requests directly from the application

---

**Ready to manage your mining operations on Windows?** Follow the installation instructions above and start monitoring your mining machines in minutes! 🚀
