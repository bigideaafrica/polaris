# Polaris Node Manager v2.0.0 - Windows

Welcome to the Windows distribution of **Polaris Node Manager v2**! This package contains optimized Windows installers and portable versions for managing your mining operations.

## 📦 Available Downloads

### Installer Version (Recommended)
- **PolarisNodeManager-Setup.exe** - Full Windows installer with shortcuts and auto-updates
- **File Size**: ~150MB
- **Installation**: Automatic with Windows integration
- **Updates**: Built-in update system

### Portable Version
- **PolarisNodeManager-Portable.zip** - No installation required
- **File Size**: ~120MB compressed
- **Installation**: Extract and run
- **Updates**: Manual download required

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

### Method 1: Using the Installer (Recommended)

#### Option A: Download and Install
1. **Download** the installer:
   ```powershell
   # Using PowerShell (recommended)
   Invoke-WebRequest -Uri "https://github.com/BANADDA/polaris_distributions/raw/main/v2/windows/PolarisNodeManager-Setup.exe" -OutFile "PolarisNodeManager-Setup.exe"
   ```

2. **Run** the installer:
   ```powershell
   # Run with administrator privileges
   Start-Process -FilePath ".\PolarisNodeManager-Setup.exe" -Verb RunAs
   ```

3. **Follow** the installation wizard:
   - Accept the license agreement
   - Choose installation directory (default: `C:\Program Files\PolarisNodeManager`)
   - Select additional components (desktop shortcut, start menu entry)
   - Complete the installation

#### Option B: Direct Installation
1. **Right-click** on `PolarisNodeManager-Setup.exe`
2. **Select** "Run as administrator"
3. **Follow** the installation prompts
4. **Launch** from Start Menu or Desktop shortcut

### Method 2: Portable Version

#### Extract and Run
1. **Download** the portable package:
   ```powershell
   # Download portable ZIP
   Invoke-WebRequest -Uri "https://github.com/BANADDA/polaris_distributions/raw/main/v2/windows/PolarisNodeManager-Portable.zip" -OutFile "PolarisNodeManager-Portable.zip"
   ```

2. **Extract** the ZIP file:
   ```powershell
   # Extract to current directory
   Expand-Archive -Path "PolarisNodeManager-Portable.zip" -DestinationPath ".\PolarisNodeManager"
   ```

3. **Navigate** to the extracted folder:
   ```cmd
   cd PolarisNodeManager
   ```

4. **Run** the application:
   ```cmd
   # Double-click or run from command line
   PolarisNodeManager.exe
   ```

## 📂 File Structure

### Installed Version
```
C:\Program Files\PolarisNodeManager\
├── PolarisNodeManager.exe          # Main application
├── resources\                       # Application resources
├── locales\                        # Language files
├── uninstall.exe                   # Uninstaller
└── README.txt                     # Quick reference
```

### Portable Version
```
PolarisNodeManager\
├── PolarisNodeManager.exe          # Main application
├── resources\                       # Application resources
├── data\                          # User data and configurations
├── logs\                          # Application logs
└── README.txt                     # Quick reference
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
- 🐛 **Issues**: [GitHub Issues](https://github.com/BANADDA/polaris_distributions/issues)

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

---

**Ready to manage your mining operations on Windows?** Follow the installation instructions above and start monitoring your mining machines in minutes! 🚀
