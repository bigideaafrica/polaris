# Polaris Node Manager v2.0.5 - Windows Distribution

**Polaris Node Manager v2.0.5** for Windows delivers critical infrastructure updates with enhanced server key management and refined endpoint configurations, ensuring optimal connectivity and improved mining performance.

## 🪟 Windows Distribution

This directory contains the Windows builds of Polaris Node Manager v2.0.5, optimized for Windows 10 and later versions.

### Available Files

- **windows-latest-build.zip** - Complete Windows application package with all dependencies included

## 🔧 What's New in v2.0.5

- **Updated Server Keys**: Enhanced server key infrastructure with improved authentication protocols
- **Endpoint Optimization**: Refined endpoint configurations for better connectivity and reduced latency
- **Infrastructure Hardening**: Server-side improvements for enhanced stability and performance
- **Connection Reliability**: Improved connection management with better failover mechanisms
- **Performance Optimizations**: Backend optimizations for faster response times and reduced overhead

## 📥 Installation

### System Requirements

- **OS**: Windows 10 (Build 20348) or later, Windows 11
- **Architecture**: x64 (64-bit)
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 1GB free disk space
- **Network**: Stable internet connection with TLS 1.3 support
- **Permissions**: Administrator privileges recommended for installation

### Quick Installation

#### Method 1: Command Prompt
```cmd
REM Download the build (using curl if available)
curl -L -o windows-latest-build.zip .\windows-latest-build.zip

REM Extract using built-in tar
tar -xf windows-latest-build.zip

REM Navigate to extracted directory
cd polaris-node-manager-windows-v2.0.5

REM Run the application
"Polaris Node Manager.exe"
```

#### Method 2: PowerShell
```powershell
# Download the build
Invoke-WebRequest -Uri ".\windows-latest-build.zip" -OutFile "windows-latest-build.zip"

# Extract the package
Expand-Archive -Path "windows-latest-build.zip" -DestinationPath ".\polaris-node-manager-windows-v2.0.5"

# Navigate to extracted directory
Set-Location ".\polaris-node-manager-windows-v2.0.5"

# Run the application
Start-Process "Polaris Node Manager.exe"
```

### Alternative Installation Methods

#### Method 3: File Explorer Installation
1. Download `windows-latest-build.zip`
2. Right-click and select "Extract All..."
3. Choose destination folder
4. Navigate to extracted folder
5. Double-click `Polaris Node Manager.exe`

#### Method 4: Direct GitHub Download
```powershell
# Download from GitHub releases
Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.5/windows-latest-build.zip" -OutFile "polaris-windows-v2.0.5.zip"

# Extract and run
Expand-Archive -Path "polaris-windows-v2.0.5.zip" -DestinationPath "C:\PolarisNodeManager"
Set-Location "C:\PolarisNodeManager"
Start-Process "Polaris Node Manager.exe"
```

## 🚀 Quick Start

1. **Download**: Get `windows-latest-build.zip` from this directory
2. **Extract**: Unzip to your preferred location (e.g., `C:\PolarisNodeManager`)
3. **Run**: Execute `Polaris Node Manager.exe`
4. **Allow**: Approve Windows Defender SmartScreen prompt if needed
5. **Setup**: Follow the in-app setup wizard to configure your mining machines

## 🔒 Security and Windows Defender

### Windows Defender SmartScreen

When running for the first time, Windows Defender SmartScreen may show a warning:

1. **If you see "Windows protected your PC"**:
   - Click "More info"
   - Click "Run anyway"
   - The application will be added to trusted list

2. **For Windows 11 users**:
   - Go to Windows Security → App & browser control
   - Add Polaris Node Manager to trusted applications

### Antivirus Considerations

Some antivirus software may flag cryptocurrency-related applications:
- **Add exception**: Add the Polaris installation folder to antivirus exclusions
- **Whitelist executable**: Add `Polaris Node Manager.exe` to trusted applications
- **Disable real-time scanning** temporarily during installation if needed

## 🪟 Windows-Specific Features

### Native Integration
- **Start Menu Integration**: Pin to Start Menu for quick access
- **System Tray**: Minimize to system tray for background operation
- **Windows Notifications**: Native toast notifications for mining status
- **File Associations**: Associate .polaris configuration files
- **Task Scheduler**: Schedule automatic startup and maintenance

### Windows Performance Features
- **Hardware Acceleration**: DirectX and OpenGL acceleration support
- **Power Management**: Optimized power usage profiles
- **Multi-Monitor**: Full support for multiple monitor setups
- **High DPI**: Native support for high-resolution displays

## 📋 Prerequisites

### Required Components

Most components are included, but you may need:

```cmd
REM Check Windows version
winver

REM Verify .NET Framework (should be included)
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full" /v Release

REM Check PowerShell version
$PSVersionTable.PSVersion
```

### Network Configuration

```cmd
REM Test HTTPS connectivity
curl -I https://polariscloud.ai

REM Check TLS support
powershell "Invoke-WebRequest -Uri https://polariscloud.ai -UseBasicParsing"

REM Verify Windows Update (for latest TLS support)
sfc /scannow
```

### Windows Features

Enable optional Windows features if needed:
```powershell
# Enable TLS 1.3 (Windows 11/Server 2022)
Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\SCHANNEL\Protocols\TLS 1.3\Client' -Name 'Enabled' -Value 1

# Check Windows firewall
Get-NetFirewallProfile

# Allow app through firewall (run as administrator)
New-NetFirewallRule -DisplayName "Polaris Node Manager" -Direction Outbound -Protocol TCP -RemotePort 443 -Action Allow
```

## 🛠️ Troubleshooting

### Common Issues

#### Application Won't Start
```cmd
REM Check if Visual C++ Redistributables are installed
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\VC\Runtimes\x64"

REM Run compatibility troubleshooter
msdt.exe -id PCWDiagnostic

REM Check Windows Event Log
eventvwr.msc
```

#### Missing DLL Errors
```powershell
# Download and install Visual C++ Redistributable
Invoke-WebRequest -Uri "https://aka.ms/vs/17/release/vc_redist.x64.exe" -OutFile "vc_redist.x64.exe"
Start-Process "vc_redist.x64.exe" -ArgumentList "/quiet" -Wait

# Install .NET 6 Desktop Runtime if needed
Invoke-WebRequest -Uri "https://download.microsoft.com/download/6/0/f/60f2237c-8140-4e51-b9ba-70d21014c0bc/windowsdesktop-runtime-6.0.14-win-x64.exe" -OutFile "dotnet-runtime.exe"
Start-Process "dotnet-runtime.exe" -ArgumentList "/quiet" -Wait
```

#### Firewall/Network Issues
```powershell
# Test network connectivity
Test-NetConnection -ComputerName polariscloud.ai -Port 443

# Temporarily disable Windows Firewall (for testing)
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled False

# Re-enable firewall after testing
Set-NetFirewallProfile -Profile Domain,Public,Private -Enabled True

# Check proxy settings
netsh winhttp show proxy
```

#### Performance Issues
```cmd
REM Check system resources
taskmgr

REM Clean temporary files
cleanmgr /sagerun:1

REM Check disk space
dir C:\ /-c

REM Update Windows (important for performance)
sconfig
```

### Advanced Troubleshooting

#### Application Logs
```powershell
# View application event logs
Get-WinEvent -LogName Application | Where-Object {$_.ProviderName -like "*Polaris*"} | Select-Object -First 10

# Check system logs for errors
Get-WinEvent -LogName System | Where-Object {$_.LevelDisplayName -eq "Error"} | Select-Object -First 5
```

#### Registry Issues
```cmd
REM Reset Windows networking stack (if network issues persist)
netsh winsock reset
netsh int ip reset

REM Repair Windows image (if system corruption suspected)
DISM /Online /Cleanup-Image /RestoreHealth
sfc /scannow
```

## 🔒 Security Best Practices

### User Account Control (UAC)
- Run as standard user for daily operation
- Use "Run as administrator" only when needed
- Consider creating dedicated mining user account

### Windows Security
```powershell
# Check Windows Defender status
Get-MpComputerStatus

# Update Windows Defender signatures
Update-MpSignature

# Perform quick scan
Start-MpScan -ScanType QuickScan
```

### Network Security
```powershell
# Enable Windows Firewall logging
Set-NetFirewallProfile -Profile Domain,Public,Private -LogFileName %SystemRoot%\System32\LogFiles\Firewall\pfirewall.log -LogMaxSizeKilobytes 4096 -LogAllowed True -LogBlocked True

# Check active network connections
Get-NetTCPConnection | Where-Object {$_.State -eq "Established"}
```

## 📊 Performance Optimization

### System Optimization
```powershell
# Set high performance power plan
powercfg /setactive SCHEME_MIN

# Disable unnecessary startup programs
Get-CimInstance Win32_StartupCommand | Select-Object Name, Command, Location

# Optimize virtual memory
# Go to: System Properties → Advanced → Performance Settings → Advanced → Virtual Memory
```

### Network Optimization
```cmd
REM Optimize TCP settings
netsh int tcp set global autotuninglevel=normal
netsh int tcp set global chimney=enabled
netsh int tcp set global rss=enabled

REM Flush DNS cache
ipconfig /flushdns

REM Reset TCP/IP stack
netsh int ip reset
```

### Hardware Acceleration
- **GPU**: Ensure latest graphics drivers are installed
- **CPU**: Enable all CPU cores in msconfig
- **RAM**: Close unnecessary applications to free memory
- **Storage**: Use SSD for installation if available

## 📞 Support

For Windows-specific issues:

- **General Support**: support@polariscloud.ai
- **Windows Issues**: windows-support@polariscloud.ai
- **GitHub Issues**: [Report Windows-specific bugs](https://github.com/bigideaafrica/polaris_distributions/issues)

When reporting issues, include:
- Windows version (`winver`)
- System specifications (`msinfo32`)
- Error messages or Event Log entries
- Network configuration (`ipconfig /all`)

## 📄 Additional Information

- **License**: MIT License
- **Version**: 2.0.5
- **Build Date**: January 2024
- **Architecture**: x64 (64-bit)
- **Minimum Windows**: Windows 10 Build 20348
- **Signed**: Code signed with valid certificate

## 🔄 Auto-Updates

Polaris Node Manager includes built-in auto-update functionality:
- Automatic check for updates on startup
- Secure download and verification of updates
- Background installation with minimal user interruption
- Automatic restart handling

### Manual Update Check
```powershell
# Check current version
Get-ItemProperty "HKLM:\SOFTWARE\PolarisCloud\NodeManager" -Name Version

# Force update check (from within application)
# Help → Check for Updates
```

---

**Note**: This Windows distribution includes all the infrastructure improvements from v2.0.5, optimized specifically for Windows environments. For the complete feature list and detailed documentation, see the main [v2.0.5 README](../README.md). 