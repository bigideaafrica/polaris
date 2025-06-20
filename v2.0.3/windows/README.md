# Polaris Node Manager v2.0.3 - Windows

**Advanced Real-Time Monitoring System for Windows**

This guide covers installation and setup of Polaris Node Manager v2.0.3 on Windows systems, featuring the new advanced monitoring capabilities.

## 📥 Download & Installation

### Quick Installation

1. **Download the Package**
   ```
   File: polaris-node-manager-windows.zip
   Size: ~174MB
   ```

2. **Extract the Archive**
   - Right-click on the downloaded ZIP file
   - Select "Extract All..." or use your preferred archive tool
   - Choose a destination folder (e.g., `C:\Program Files\Polaris Node Manager`)

3. **Run the Application**
   - Navigate to the extracted folder
   - Double-click `Polaris Node Manager.exe` to launch

### Alternative Installation Methods

#### Command Prompt Installation
```cmd
cd Downloads
tar -xf polaris-node-manager-windows.zip
cd polaris-node-manager-windows
"Polaris Node Manager.exe"
```

#### PowerShell Installation
```powershell
cd Downloads
Expand-Archive -Path polaris-node-manager-windows.zip -DestinationPath .
cd polaris-node-manager-windows
& ".\Polaris Node Manager.exe"
```

## 🚀 New Monitoring Features in v2.0.3

### **Windows-Specific Monitoring Enhancements**

#### **Connection Monitoring**
- **Windows Firewall Integration**: Automatic detection of Windows Firewall rules affecting connectivity
- **Network Adapter Monitoring**: Real-time monitoring of active network adapters
- **VPN Detection**: Identifies when VPN connections might affect mining connectivity
- **Port Status Checking**: Validates that required ports are open and accessible

#### **Authentication Monitoring**
- **Windows SSH Client Support**: Full compatibility with Windows 10/11 built-in OpenSSH client
- **PuTTY Integration**: Support for PuTTY-generated SSH keys and authentication
- **Windows Credential Manager**: Secure storage integration for SSH credentials
- **Domain Authentication**: Support for domain-joined machines and authentication

#### **Performance Monitoring (PoW)**
- **Windows Performance Counters**: Integration with Windows system performance monitoring
- **GPU Monitoring**: Enhanced NVIDIA/AMD GPU detection and performance tracking on Windows
- **CPU Temperature Monitoring**: Windows-specific temperature sensor integration
- **Memory Usage Tracking**: Detailed Windows memory usage analysis for mining processes

#### **Docker Environment Monitoring**
- **Docker Desktop Integration**: Full support for Docker Desktop on Windows
- **WSL2 Backend Monitoring**: Monitoring of WSL2 backend status for Docker
- **Hyper-V Integration**: Checks for Hyper-V requirements and status
- **Container Resource Limits**: Windows-specific container resource monitoring

## 🖥️ Windows System Requirements

### **Minimum Requirements**
- **Operating System**: Windows 10 version 1903 or later, Windows 11
- **Architecture**: x64 (64-bit) required
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 1GB free space for application and monitoring data
- **Network**: Stable internet connection with unrestricted outbound access

### **Recommended for Optimal Monitoring**
- **Windows 11**: Latest version for best monitoring integration
- **RAM**: 16GB for monitoring multiple high-performance machines
- **SSD Storage**: For faster monitoring data processing and caching
- **Dedicated Network**: Ethernet connection for stable monitoring connectivity

### **For Mining Machines (Windows)**
- **Docker Desktop**: Latest version with WSL2 backend enabled
- **OpenSSH Server**: Windows OpenSSH server feature enabled
- **Windows Defender**: Properly configured with mining software exceptions
- **User Account Control (UAC)**: Configured for automated task execution

## 🔧 Windows-Specific Setup

### **1. Enable Required Windows Features**

#### Enable OpenSSH Server (for mining machines)
```powershell
# Run as Administrator
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
Start-Service sshd
Set-Service -Name sshd -StartupType 'Automatic'
```

#### Enable OpenSSH Client (for management machine)
```powershell
# Run as Administrator
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

### **2. Configure Windows Firewall**

#### Allow Polaris Node Manager through firewall
```powershell
# Run as Administrator
New-NetFirewallRule -DisplayName "Polaris Node Manager" -Direction Inbound -Program "C:\Path\To\Polaris Node Manager.exe" -Action Allow
New-NetFirewallRule -DisplayName "Polaris Node Manager" -Direction Outbound -Program "C:\Path\To\Polaris Node Manager.exe" -Action Allow
```

#### Configure SSH access (for mining machines)
```powershell
# Run as Administrator
New-NetFirewallRule -DisplayName "SSH Server" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow
```

### **3. Install Docker Desktop (for mining machines)**

1. Download Docker Desktop from [docker.com](https://www.docker.com/products/docker-desktop)
2. Install with WSL2 backend enabled
3. Ensure Docker is running and accessible

## 📊 Windows Monitoring Dashboard

### **Windows-Specific Status Indicators**

#### **System Health Panel**
- **Windows Update Status**: Checks for pending updates that might affect performance
- **System Uptime**: Monitors system stability and restart requirements
- **Disk Health**: SMART status monitoring for system drives
- **Event Log Monitoring**: Checks Windows Event Log for critical errors

#### **Network Monitoring**
- **Network Adapter Status**: Real-time status of all network interfaces
- **DNS Resolution**: Monitors DNS resolution performance
- **Internet Connectivity**: Validates internet access and routing
- **Bandwidth Utilization**: Tracks network usage for mining operations

#### **Performance Monitoring**
- **CPU Usage**: Real-time CPU utilization with per-core breakdown
- **Memory Usage**: Physical and virtual memory utilization
- **GPU Status**: NVIDIA/AMD GPU temperature, utilization, and memory usage
- **Storage I/O**: Disk read/write performance and queue length

## 🛠️ Windows-Specific Troubleshooting

### **Common Windows Issues**

#### **Connection Problems**
- **Windows Firewall Blocking**: Check Windows Defender Firewall settings
- **Antivirus Interference**: Add Polaris Node Manager to antivirus exceptions
- **Network Profile Issues**: Ensure network is set to Private, not Public
- **VPN Conflicts**: Disable VPN temporarily to test connectivity

#### **Authentication Issues**
- **SSH Service Not Running**: Start OpenSSH Server service
- **Key Permissions**: Check SSH key file permissions in Windows
- **User Account Issues**: Ensure SSH user has proper Windows permissions
- **Domain Authentication**: Configure domain authentication if applicable

#### **Performance Issues**
- **Windows Updates**: Install pending Windows updates
- **Driver Updates**: Update GPU and system drivers
- **Power Management**: Set power plan to High Performance
- **Background Apps**: Disable unnecessary Windows background applications

#### **Docker Issues**
- **WSL2 Not Enabled**: Enable WSL2 feature in Windows
- **Hyper-V Conflicts**: Resolve Hyper-V and VirtualBox conflicts
- **Docker Service**: Restart Docker Desktop service
- **Resource Limits**: Adjust Docker Desktop resource allocation

### **Windows Event Log Integration**

The monitoring system integrates with Windows Event Log:
- **Application Events**: Monitors Polaris-related application events
- **System Events**: Tracks system-level events affecting mining
- **Security Events**: Monitors authentication and security events
- **Custom Events**: Creates custom event log entries for monitoring milestones

## 🔒 Windows Security Features

### **Enhanced Security Monitoring**
- **Windows Defender Integration**: Monitors antivirus status and exceptions
- **BitLocker Status**: Checks disk encryption status for security compliance
- **User Account Control**: Monitors UAC events and privilege escalation
- **Network Security**: Windows Firewall rule monitoring and validation

### **Credential Security**
- **Windows Credential Manager**: Secure storage for SSH keys and passwords
- **Certificate Store Integration**: Uses Windows certificate store for SSL/TLS
- **Encrypted Storage**: All monitoring data encrypted using Windows DPAPI
- **Access Control**: Windows ACL integration for file and registry permissions

## 📈 Performance Optimization for Windows

### **Windows-Specific Optimizations**
- **Windows Services**: Optimize Windows services for mining performance
- **Registry Tuning**: Apply registry optimizations for network and performance
- **Process Priority**: Automatic process priority management for mining tasks
- **Memory Management**: Windows memory management optimization for large datasets

### **Monitoring Efficiency**
- **Windows Performance Toolkit**: Integration with WPT for advanced monitoring
- **ETW (Event Tracing for Windows)**: Low-overhead system monitoring
- **Performance Counters**: Efficient use of Windows performance counters
- **WMI Integration**: Windows Management Instrumentation for system data

## 🆘 Windows Support Resources

### **Windows-Specific Help**
- **PowerShell Scripts**: Automated diagnostic and setup scripts
- **Windows Event Viewer**: Guide to reading Polaris-related events
- **Performance Monitor**: Using Windows Performance Monitor with Polaris
- **Resource Monitor**: Monitoring system resources during mining operations

### **Common Windows Commands**
```powershell
# Check SSH service status
Get-Service sshd

# Test network connectivity
Test-NetConnection -ComputerName "your-mining-machine" -Port 22

# Check Docker status
docker version
docker ps

# Monitor system performance
Get-Counter "\Processor(_Total)\% Processor Time"
```

## 🔄 Upgrading from Previous Versions

### **From v2.0.2 on Windows**
- **In-Place Upgrade**: Extract new version over existing installation
- **Settings Migration**: Windows settings automatically migrated
- **Registry Preservation**: Windows registry settings preserved
- **Service Continuity**: Windows services updated without interruption

### **Windows-Specific Migration Notes**
- **Firewall Rules**: Existing firewall rules are preserved
- **Scheduled Tasks**: Windows Task Scheduler entries updated automatically
- **User Permissions**: Windows user permissions and group memberships maintained
- **Certificate Store**: SSL certificates and keys preserved in Windows certificate store

---

**Polaris Node Manager v2.0.3 for Windows** provides the most comprehensive mining management experience with advanced Windows-specific monitoring capabilities. Take advantage of deep Windows integration for optimal mining performance and monitoring.

For Windows-specific support, consult the Windows Event Viewer for detailed error information and use the built-in diagnostic tools provided with the application. 