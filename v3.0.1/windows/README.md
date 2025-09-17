# Polaris Node Manager v3.0.1 - Windows

Windows distribution of Polaris Node Manager v3.0.1 with native Windows integration, WSL2 support, and enterprise-grade Windows security features.

## 📦 Available Downloads

### Windows Latest Build
- **File**: `windows-latest-build.zip`
- **Architecture**: x64 (AMD64) with ARM64 support
- **Format**: Universal ZIP containing MSI installer and portable executable
- **Size**: ~180MB (compressed)
- **Compatibility**: Windows 10 version 1909+ / Windows 11

## 🔧 Installation Options

### Option 1: MSI Installer (Recommended)

1. **Extract the ZIP file**:
   ```powershell
   Expand-Archive -Path windows-latest-build.zip -DestinationPath C:\temp\polaris\
   ```

2. **Run the MSI installer** (as Administrator):
   ```powershell
   Start-Process -FilePath "C:\temp\polaris\Polaris-Node-Manager-v3.0.1.msi" -Verb RunAs
   ```

3. **Follow the installation wizard**:
   - Choose installation directory (default: `C:\Program Files\Polaris Node Manager\`)
   - Select components to install
   - Configure Windows integration options

4. **Launch from Start Menu**:
   - Search for "Polaris Node Manager"
   - Or run from Command Prompt: `polaris`

### Option 2: Portable Installation

1. **Extract the ZIP file**:
   ```powershell
   Expand-Archive -Path windows-latest-build.zip -DestinationPath C:\polaris\
   ```

2. **Run the portable executable**:
   ```powershell
   cd C:\polaris\
   .\Polaris-Node-Manager.exe
   ```

3. **Create desktop shortcut** (optional):
   ```powershell
   $WshShell = New-Object -comObject WScript.Shell
   $Shortcut = $WshShell.CreateShortcut("$Home\Desktop\Polaris Node Manager.lnk")
   $Shortcut.TargetPath = "C:\polaris\Polaris-Node-Manager.exe"
   $Shortcut.Save()
   ```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: Windows 10 version 1909 or later (Windows 11 recommended)
- **Architecture**: x64 (AMD64) - ARM64 support available
- **RAM**: 16GB minimum (32GB recommended for enterprise workloads)
- **Storage**: 10GB free disk space (SSD recommended)
- **CPU**: 4 cores minimum (8+ cores recommended)
- **Network**: Broadband internet connection

### Recommended Requirements
- **OS**: Windows 11 with latest updates
- **RAM**: 32GB or more
- **CPU**: Intel Core i7/AMD Ryzen 7 or better
- **Storage**: 50GB+ NVMe SSD storage
- **GPU**: NVIDIA RTX 3060 or better (for AI workloads)

### Required Windows Features
- **Windows Subsystem for Linux (WSL2)**: For container support
- **Hyper-V**: For virtual machine management
- **Windows Terminal**: Enhanced command-line experience
- **.NET 6.0 Runtime**: For application framework support

## 🔧 Prerequisites Setup

### Enable WSL2 and Hyper-V

Run PowerShell as Administrator and execute:

```powershell
# Enable WSL2
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Enable Hyper-V
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All

# Set WSL2 as default
wsl --set-default-version 2

# Restart required
Restart-Computer
```

### Install Ubuntu for WSL2

```powershell
# Install Ubuntu 22.04 LTS
wsl --install -d Ubuntu-22.04

# Or from Microsoft Store
start ms-windows-store://pdp/?ProductId=9PN20MSR04DW
```

### Install Docker Desktop

1. **Download Docker Desktop**: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. **Install with WSL2 backend enabled**
3. **Configure Docker settings**:
   - Enable WSL2 integration
   - Allocate sufficient resources (8GB+ RAM)
   - Enable Kubernetes (optional)

### Install Windows Terminal

```powershell
# Install via Microsoft Store
start ms-windows-store://pdp/?ProductId=9N0DX20HK701

# Or via winget
winget install Microsoft.WindowsTerminal
```

## 🚀 First-Time Setup

### 1. Launch Polaris Node Manager

```powershell
# From Start Menu
Start-Process "Polaris Node Manager"

# Or from Command Prompt
polaris
```

### 2. Complete Setup Wizard

1. **Welcome Screen**: Choose setup type (Quick/Custom)
2. **Cloud Provider Configuration**:
   - Add AWS, Azure, or GCP credentials
   - Configure multi-cloud settings
3. **Windows Integration**:
   - Enable Windows security integration
   - Configure Windows Defender exclusions
   - Set up PowerShell integration
4. **AI Features Setup**:
   - Enable AI-powered optimization
   - Configure natural language interface
   - Set up predictive analytics

### 3. Windows-Specific Configuration

```powershell
# Configure Windows Defender exclusions
polaris windows configure-defender

# Set up PowerShell integration
polaris windows setup-powershell

# Configure Windows services
polaris windows install-services
```

## 🛡️ Windows Security Integration

### Windows Defender Integration
- **Automatic Exclusions**: Polaris automatically configures Windows Defender exclusions
- **Real-time Scanning**: Integration with Windows Security for real-time threat detection
- **SmartScreen Integration**: Enhanced SmartScreen protection for downloaded content

### Windows Security Features
- **Windows Hello**: Biometric authentication support
- **Windows Credential Manager**: Secure credential storage
- **BitLocker Integration**: Full disk encryption support
- **Windows Firewall**: Automatic firewall rule configuration

### Enterprise Security (Windows Pro/Enterprise)
- **Group Policy Support**: Enterprise policy management
- **Active Directory Integration**: Seamless AD authentication
- **Certificate Store Integration**: Windows certificate store management
- **Windows Event Log**: Comprehensive audit logging

## 🔧 Windows-Specific Features

### PowerShell Integration
```powershell
# Import Polaris PowerShell module
Import-Module PolarisNodeManager

# Get cluster status
Get-PolarisClusterStatus

# Deploy template
Deploy-PolarisTemplate -Name "webapp" -Provider "azure"

# Manage resources
Get-PolarisResources | Where-Object {$_.Status -eq "Running"}
```

### Windows Service Management
```powershell
# Install Polaris as Windows Service
polaris service install

# Start/Stop service
Start-Service "PolarisNodeManager"
Stop-Service "PolarisNodeManager"

# Check service status
Get-Service "PolarisNodeManager"
```

### Task Scheduler Integration
- **Automatic Updates**: Scheduled update checks and installations
- **Backup Tasks**: Automated configuration and data backups
- **Maintenance Tasks**: Regular maintenance and optimization tasks

## 🐳 Container Management on Windows

### Docker Desktop Configuration
```powershell
# Configure Docker for Polaris
polaris docker configure

# Enable Kubernetes
polaris k8s enable-windows

# Set up Windows containers
polaris containers enable-windows-containers
```

### WSL2 Integration
```powershell
# Configure WSL2 for Polaris
polaris wsl configure

# Install Linux tools in WSL2
wsl -d Ubuntu-22.04 -- sudo apt update
wsl -d Ubuntu-22.04 -- sudo apt install -y docker.io kubectl helm
```

### Hyper-V Virtual Machines
- **VM Templates**: Pre-configured VM templates for various workloads
- **Snapshot Management**: Automatic VM snapshots and rollback
- **Network Configuration**: Advanced virtual networking setup

## 🔄 Updates and Maintenance

### Automatic Updates
- **Windows Update Integration**: Updates delivered through Windows Update
- **Background Updates**: Automatic background updates with user notification
- **Rollback Support**: Easy rollback to previous versions if needed

### Manual Updates
```powershell
# Check for updates
polaris update check

# Download and install updates
polaris update install

# Update with specific version
polaris update install --version 3.0.2
```

### Maintenance Tasks
```powershell
# Run system diagnostics
polaris system diagnose

# Clean temporary files
polaris system cleanup

# Optimize performance
polaris system optimize

# Backup configuration
polaris backup create --location "C:\PolarisBackups\"
```

## 🐛 Troubleshooting

### Common Windows Issues

**WSL2 Not Working**:
```powershell
# Check WSL2 status
wsl --status

# Update WSL2 kernel
wsl --update

# Restart WSL2
wsl --shutdown
wsl
```

**Docker Desktop Issues**:
```powershell
# Restart Docker Desktop
Stop-Process -Name "Docker Desktop" -Force
Start-Process "C:\Program Files\Docker\Docker\Docker Desktop.exe"

# Reset Docker Desktop
& "C:\Program Files\Docker\Docker\DockerCli.exe" -SwitchDaemon system factory-reset
```

**Windows Firewall Blocking Connections**:
```powershell
# Add Polaris firewall rules
New-NetFirewallRule -DisplayName "Polaris API" -Direction Inbound -Protocol TCP -LocalPort 8080 -Action Allow
New-NetFirewallRule -DisplayName "Polaris SSH" -Direction Inbound -Protocol TCP -LocalPort 22 -Action Allow

# Or use Polaris built-in configuration
polaris windows configure-firewall
```

**PowerShell Execution Policy Issues**:
```powershell
# Set execution policy for current user
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Or bypass for Polaris scripts
powershell -ExecutionPolicy Bypass -File "C:\Program Files\Polaris Node Manager\scripts\setup.ps1"
```

### Performance Optimization

**Resource Allocation**:
```powershell
# Configure WSL2 memory allocation
echo '[wsl2]
memory=16GB
processors=8' | Out-File -FilePath "$env:USERPROFILE\.wslconfig" -Encoding ascii

# Restart WSL2
wsl --shutdown
```

**Docker Resource Limits**:
- Open Docker Desktop Settings
- Navigate to Resources
- Adjust CPU and Memory allocation
- Apply and restart Docker

### Log Files and Diagnostics
- **Application Logs**: `%LOCALAPPDATA%\Polaris\logs\`
- **System Logs**: Windows Event Viewer → Applications and Services → Polaris
- **Docker Logs**: `docker logs polaris-node-manager`
- **WSL2 Logs**: `wsl -d Ubuntu-22.04 -- journalctl -u polaris`

## 📚 Windows-Specific Resources

### Documentation
- **Windows Installation Guide**: [docs.polaris.bigideaafrica.com/windows](https://docs.polaris.bigideaafrica.com/windows)
- **PowerShell Module Documentation**: [docs.polaris.bigideaafrica.com/powershell](https://docs.polaris.bigideaafrica.com/powershell)
- **Windows Security Guide**: [docs.polaris.bigideaafrica.com/security/windows](https://docs.polaris.bigideaafrica.com/security/windows)

### Community Resources
- **Windows Users Forum**: [community.polaris.bigideaafrica.com/c/windows](https://community.polaris.bigideaafrica.com/c/windows)
- **PowerShell Scripts Repository**: [github.com/bigideaafrica/polaris-powershell](https://github.com/bigideaafrica/polaris-powershell)
- **Windows Best Practices**: [guides.polaris.bigideaafrica.com/windows](https://guides.polaris.bigideaafrica.com/windows)

## 📞 Windows Support

### Windows-Specific Support
- **Windows Technical Support**: windows-support@polaris.bigideaafrica.com
- **PowerShell Integration Support**: powershell-support@polaris.bigideaafrica.com
- **Enterprise Windows Support**: enterprise-windows@polaris.bigideaafrica.com

### Microsoft Partnership
Polaris Node Manager is a Microsoft Partner solution with:
- **Azure Certified**: Certified for Azure deployments
- **Windows Compatible**: Windows Hardware Quality Labs (WHQL) tested
- **Microsoft Store**: Available through Microsoft Store for Business

---

**Build Information**:
- **Build Date**: Latest development build
- **Compiler**: Visual Studio 2022 with MSVC v143
- **Target Framework**: .NET 6.0 with Windows-specific optimizations
- **Package Format**: MSI installer + portable executable
- **Dependencies**: Bundled with Windows Runtime requirements

**Note**: For the best experience on Windows, we recommend using Windows 11 with the latest updates and enabling all suggested Windows features during installation.
