# Polaris Node Manager v3.0.0 - Windows

Windows distribution of Polaris Node Manager v3.0.0 with comprehensive support for Windows 10/11 and enhanced container orchestration capabilities.

## 📦 Available Downloads

### Windows Latest Build
- **File**: `windows-latest-build.zip`
- **Architecture**: x64 (AMD64) with ARM64 support
- **Format**: ZIP containing MSI installer and portable executable
- **Size**: ~180MB (compressed)
- **Compatibility**: Windows 10 version 1909+ and Windows 11

## 🔧 Installation

### Quick Installation (Recommended)

1. **Download and Extract**:
   ```powershell
   # Using PowerShell
   Invoke-WebRequest -Uri "[download-url]" -OutFile "polaris-v3-windows.zip"
   Expand-Archive -Path "polaris-v3-windows.zip" -DestinationPath ".\polaris-v3\"
   ```

2. **Run MSI Installer**:
   ```powershell
   cd polaris-v3
   .\PolarisNodeManager-v3.0.0-x64.msi
   ```

3. **Launch Application**:
   - From Start Menu: "Polaris Node Manager"
   - From Desktop shortcut
   - Or via Command Prompt: `polaris-node-manager`

### Portable Installation

1. **Extract ZIP file**:
   ```powershell
   Expand-Archive -Path "windows-latest-build.zip" -DestinationPath "C:\Polaris\"
   ```

2. **Run Portable Executable**:
   ```powershell
   cd C:\Polaris\
   .\PolarisNodeManager.exe
   ```

3. **Create Desktop Shortcut** (optional):
   ```powershell
   $WshShell = New-Object -comObject WScript.Shell
   $Shortcut = $WshShell.CreateShortcut("$Home\Desktop\Polaris Node Manager.lnk")
   $Shortcut.TargetPath = "C:\Polaris\PolarisNodeManager.exe"
   $Shortcut.Save()
   ```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: Windows 10 version 1909 (Build 18363) or later
- **Architecture**: x64 (AMD64) or ARM64
- **RAM**: 8GB minimum (16GB recommended)
- **Storage**: 5GB free disk space
- **Network**: Broadband internet connection
- **.NET**: .NET 6.0 Runtime (included in installer)

### Recommended Requirements
- **OS**: Windows 11 (latest version)
- **RAM**: 16GB or more
- **CPU**: Intel Core i5/i7 or AMD Ryzen 5/7 (4+ cores)
- **Storage**: 20GB+ SSD storage
- **GPU**: Dedicated GPU for AI workloads (optional)
- **Network**: High-speed internet (50+ Mbps)

### Windows Version Compatibility
- ✅ **Windows 11**: Full support with enhanced features
- ✅ **Windows 10**: Version 1909+ (Build 18363+)
- ✅ **Windows Server**: 2019, 2022
- ❌ **Windows 8.1**: Not supported
- ❌ **Windows 7**: Not supported

## 🏢 Windows-Specific Features

### Native Integration
- **Windows Services**: Background service management
- **Task Scheduler**: Automated task scheduling
- **Windows Defender**: Whitelisted for security
- **Event Viewer**: Comprehensive logging integration
- **PowerShell**: Native PowerShell cmdlets and scripts
- **Windows Terminal**: Enhanced terminal experience

### Enterprise Features
- **Group Policy**: Enterprise deployment and configuration
- **Active Directory**: Domain authentication support
- **Windows Update**: Managed updates through WSUS
- **Hyper-V Integration**: Native virtualization support
- **Windows Containers**: Docker Windows containers

## 🔧 Prerequisites & Dependencies

### Required Components
The installer will automatically install these if missing:

```powershell
# .NET 6.0 Runtime
# Visual C++ Redistributable 2022
# Windows Subsystem for Linux (WSL2) - Optional but recommended
```

### Docker Desktop for Windows
```powershell
# Download and install Docker Desktop
# Enable WSL2 backend for better performance
# Configure resource allocation: 8GB RAM, 4 CPUs minimum

# Verify installation
docker --version
docker-compose --version
```

### Windows Subsystem for Linux (WSL2)
```powershell
# Enable WSL2 (requires admin privileges)
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Restart computer, then set WSL2 as default
wsl --set-default-version 2

# Install Ubuntu distribution
wsl --install -d Ubuntu
```

## 🚀 Quick Start

1. **Launch Polaris Node Manager**:
   - Click Start Menu → "Polaris Node Manager"
   - Or press `Win + R`, type `polaris-node-manager`, press Enter

2. **Windows-Specific Setup**:
   - Grant Windows Defender permissions
   - Configure Windows Firewall rules
   - Set up Docker Desktop integration

3. **Complete Initial Configuration**:
   - Follow the Windows-optimized setup wizard
   - Configure cloud provider credentials
   - Test container deployment

## 🔒 Security & Permissions

### Windows Defender Configuration
```powershell
# Add exclusion for Polaris installation directory (as Administrator)
Add-MpPreference -ExclusionPath "C:\Program Files\Polaris Node Manager"
Add-MpPreference -ExclusionPath "$env:APPDATA\Polaris"

# Add exclusion for Docker directories
Add-MpPreference -ExclusionPath "C:\ProgramData\Docker"
Add-MpPreference -ExclusionPath "$env:USERPROFILE\.docker"
```

### Windows Firewall Rules
```powershell
# Allow Polaris through Windows Firewall (as Administrator)
New-NetFirewallRule -DisplayName "Polaris Node Manager" -Direction Inbound -Program "C:\Program Files\Polaris Node Manager\PolarisNodeManager.exe" -Action Allow

# Allow Docker Desktop
New-NetFirewallRule -DisplayName "Docker Desktop" -Direction Inbound -Program "C:\Program Files\Docker\Docker\Docker Desktop.exe" -Action Allow
```

### User Account Control (UAC)
- **Standard User**: Most operations work without admin privileges
- **Administrator**: Required for system-wide configuration
- **Service Installation**: Requires elevated privileges

## 🐳 Container Management

### Docker Desktop Integration
- **Windows Containers**: Support for Windows-based containers
- **Linux Containers**: WSL2-based Linux container support
- **Kubernetes**: Built-in Kubernetes cluster
- **Resource Management**: GUI-based resource allocation

### Hyper-V Support
```powershell
# Enable Hyper-V (Windows Pro/Enterprise)
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All

# Verify Hyper-V status
Get-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V
```

## 🔄 Updates & Maintenance

### Automatic Updates
- **Windows Update Integration**: Updates through Windows Update
- **Background Service**: Automatic update checking
- **Scheduled Updates**: Configurable update schedule
- **Rollback Support**: System restore point creation

### Manual Updates
```powershell
# Check current version
& "C:\Program Files\Polaris Node Manager\PolarisNodeManager.exe" --version

# Download latest version
Invoke-WebRequest -Uri "[latest-download-url]" -OutFile "polaris-v3-latest.zip"

# Backup current configuration
Copy-Item -Path "$env:APPDATA\Polaris" -Destination "$env:USERPROFILE\Desktop\polaris-backup" -Recurse

# Install new version
Expand-Archive -Path "polaris-v3-latest.zip" -DestinationPath ".\polaris-update\"
.\polaris-update\PolarisNodeManager-v3.0.0-x64.msi
```

## 🐛 Troubleshooting

### Common Issues

**Installation fails with "Access Denied"**:
```powershell
# Run as Administrator
Start-Process powershell -Verb runAs
# Then run the installer
```

**Docker connection failed**:
```powershell
# Start Docker Desktop
Start-Process "C:\Program Files\Docker\Docker\Docker Desktop.exe"

# Verify Docker is running
docker info

# Restart Docker service if needed
Restart-Service docker
```

**Windows Defender blocking application**:
```powershell
# Add exclusion (as Administrator)
Add-MpPreference -ExclusionPath "C:\Program Files\Polaris Node Manager"

# Check Windows Defender logs
Get-WinEvent -FilterHashtable @{LogName='Microsoft-Windows-Windows Defender/Operational'}
```

**Network connectivity issues**:
```powershell
# Test DNS resolution
nslookup api.polaris.bigideaafrica.com

# Test HTTPS connectivity
Invoke-WebRequest -Uri "https://api.polaris.bigideaafrica.com/health"

# Check Windows Firewall
Get-NetFirewallRule -DisplayName "*Polaris*"
```

**WSL2 integration problems**:
```powershell
# Update WSL2
wsl --update

# Restart WSL2
wsl --shutdown
wsl

# Reset Docker Desktop WSL integration
# Docker Desktop → Settings → Resources → WSL Integration
```

### Log Files
Application logs are stored in:
- **Application Logs**: `%APPDATA%\Polaris\logs\`
- **System Logs**: `C:\ProgramData\Polaris\logs\`
- **Windows Event Logs**: Event Viewer → Applications and Services Logs → Polaris
- **Docker Logs**: `%USERPROFILE%\.docker\`

## 🎯 Performance Optimization

### System Configuration
```powershell
# Optimize for performance
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\PriorityControl" -Name "Win32PrioritySeparation" -Value 2

# Increase virtual memory (if needed)
# Control Panel → System → Advanced → Performance Settings → Advanced → Virtual Memory
```

### Docker Performance
- **WSL2 Backend**: Use WSL2 for better Linux container performance
- **Resource Allocation**: Assign adequate CPU and memory
- **Disk Space**: Monitor Docker disk usage
- **Image Cleanup**: Regular cleanup of unused images

## 📚 Additional Resources

- **Documentation**: [docs.polaris.bigideaafrica.com/windows](https://docs.polaris.bigideaafrica.com/windows)
- **Windows-specific guides**: [guides.polaris.bigideaafrica.com/windows](https://guides.polaris.bigideaafrica.com/windows)
- **PowerShell modules**: [PowerShell Gallery](https://www.powershellgallery.com/packages/PolarisNodeManager)
- **Video tutorials**: [YouTube Channel](https://youtube.com/polarismanager)
- **Community forum**: [community.polaris.bigideaafrica.com](https://community.polaris.bigideaafrica.com)

## 📞 Support

For Windows-specific issues:
- **GitHub Issues**: [Report a bug](https://github.com/bigideaafrica/polaris_distributions/issues)
- **Community Support**: [Windows Discussion Forum](https://community.polaris.bigideaafrica.com/c/windows)
- **Email Support**: support@polaris.bigideaafrica.com
- **Documentation**: [Windows Installation Guide](https://docs.polaris.bigideaafrica.com/installation/windows)

## 🏷️ Version Information

- **Version**: 3.0.0 (Development Build)
- **Build Date**: Latest development snapshot
- **Architecture**: x64 (AMD64) with ARM64 support
- **Minimum Windows**: 10 version 1909 (Build 18363)
- **Dependencies**: .NET 6.0, Visual C++ 2022 Redistributable
- **Code Signature**: Authenticode signed for security

---

**Microsoft, Windows, and related terms are trademarks of Microsoft Corporation.**
