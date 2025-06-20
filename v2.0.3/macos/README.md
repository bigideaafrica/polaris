# Polaris Node Manager v2.0.3 - macOS

**Advanced Real-Time Monitoring System for macOS**

This guide covers installation and setup of Polaris Node Manager v2.0.3 on macOS systems, featuring comprehensive monitoring capabilities optimized for macOS environments.

## 📥 Download & Installation

### Quick Installation

1. **Download the Package**
   ```
   File: polaris-node-manager-macos.zip
   Size: ~891MB
   ```

2. **Extract and Install**
   ```bash
   # Extract the archive
   unzip polaris-node-manager-macos.zip
   cd polaris-node-manager-macos
   
   # Mount and install DMG
   open polaris-node-manager.dmg
   # Drag Polaris Node Manager to Applications folder
   ```

### Installation Methods

#### DMG Installer (Recommended)
```bash
# Download and install
curl -L https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.3/polaris-node-manager-macos.zip -o polaris-node-manager-macos.zip
unzip polaris-node-manager-macos.zip
open polaris-node-manager.dmg
```

#### Homebrew Cask (If Available)
```bash
# Install via Homebrew
brew install --cask polaris-node-manager
```

#### Direct App Bundle
```bash
# Extract and run directly
unzip polaris-node-manager-macos.zip
open "Polaris Node Manager.app"
```

## 🚀 New Monitoring Features in v2.0.3

### **macOS-Specific Monitoring Enhancements**

#### **Connection Monitoring**
- **pfctl Integration**: Real-time packet filter firewall monitoring and validation
- **Network Framework**: Native macOS Network Framework integration for connectivity testing
- **Bonjour/mDNS**: Local network discovery and service monitoring
- **Network Location Awareness**: Automatic network location detection and adaptation

#### **Authentication Monitoring**
- **Keychain Integration**: Secure credential storage and retrieval via macOS Keychain
- **Touch ID/Face ID Support**: Biometric authentication for enhanced security
- **SSH Agent Integration**: Native ssh-agent support with Keychain integration
- **Certificate Management**: macOS Certificate Assistant integration for SSL/TLS

#### **Performance Monitoring (PoW)**
- **Activity Monitor Integration**: Native macOS performance monitoring integration
- **Metal Performance Shaders**: GPU performance monitoring via Metal framework
- **Thermal State Monitoring**: macOS thermal state and throttling detection
- **Power Management**: Battery and power adapter status monitoring for MacBooks
- **CPU Frequency Monitoring**: Real-time CPU frequency and P-state monitoring

#### **Docker Environment Monitoring**
- **Docker Desktop Integration**: Full Docker Desktop for Mac monitoring and management
- **HyperKit Monitoring**: Lightweight virtualization monitoring for Docker
- **File System Events**: Native FSEvents monitoring for container file changes
- **Resource Usage**: macOS-specific resource usage monitoring for containers

## 🖥️ macOS System Requirements

### **Minimum Requirements**
- **Operating System**: macOS 10.15 Catalina or later
- **Architecture**: Intel x64 or Apple Silicon (M1/M2/M3)
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 2GB free space for application and monitoring data
- **Network**: Stable internet connection with outbound HTTPS access

### **Recommended for Optimal Monitoring**
- **macOS Version**: macOS 12 Monterey or later for best monitoring integration
- **Architecture**: Apple Silicon (M1/M2/M3) for optimal performance
- **RAM**: 16GB for monitoring multiple high-performance machines
- **SSD Storage**: Built-in SSD for faster monitoring data processing
- **Network**: Ethernet or high-speed Wi-Fi for stable monitoring connectivity

### **For Mining Machines (macOS)**
- **Docker Desktop**: Latest Docker Desktop for Mac
- **SSH Server**: Remote Login enabled in System Preferences
- **Xcode Command Line Tools**: For development tools and utilities
- **Homebrew**: Package manager for additional tools and dependencies

## 🔧 macOS-Specific Setup

### **1. Enable Required macOS Features**

#### Enable Remote Login (SSH Server)
```bash
# Enable SSH server
sudo systemsetup -setremotelogin on

# Verify SSH is running
sudo launchctl list | grep ssh
```

#### Install Xcode Command Line Tools
```bash
# Install command line tools
xcode-select --install
```

#### Install Homebrew (Recommended)
```bash
# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### **2. Install Docker Desktop**

#### Download and Install
1. Download Docker Desktop from [docker.com](https://www.docker.com/products/docker-desktop)
2. Install Docker Desktop for Mac
3. Start Docker Desktop and complete setup
4. Verify installation:
   ```bash
   docker version
   docker run hello-world
   ```

### **3. Configure macOS Security**

#### Allow Application in Security & Privacy
1. Open System Preferences → Security & Privacy
2. Allow "Polaris Node Manager" if blocked
3. Grant necessary permissions for monitoring

#### Configure Firewall (if enabled)
```bash
# Check firewall status
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate

# Allow Polaris Node Manager through firewall
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add "/Applications/Polaris Node Manager.app"
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp "/Applications/Polaris Node Manager.app"
```

## 📊 macOS Monitoring Dashboard

### **macOS-Specific Status Indicators**

#### **System Health Panel**
- **macOS Version**: Monitors macOS version and available updates
- **System Uptime**: Tracks system stability and sleep/wake cycles
- **Disk Health**: SMART monitoring and SSD health status
- **Console Monitoring**: macOS Console log monitoring for critical events

#### **Hardware Monitoring**
- **Thermal Management**: Real-time temperature monitoring and thermal throttling
- **Battery Status**: Battery health, charge cycles, and power adapter status (MacBooks)
- **Memory Pressure**: macOS memory pressure monitoring and swap usage
- **CPU Performance**: P-state monitoring and frequency scaling

#### **Network Monitoring**
- **Wi-Fi Status**: Wi-Fi signal strength, channel, and connection quality
- **Ethernet Status**: Ethernet link status and speed detection
- **VPN Detection**: Automatic VPN connection detection and status
- **Network Locations**: Active network location and configuration monitoring

#### **Application Monitoring**
- **Sandboxing**: App Sandbox status and permission monitoring
- **Code Signing**: Application signature verification and trust status
- **Notarization**: Notarization status for enhanced security
- **Resource Usage**: Per-application resource usage via Activity Monitor APIs

## 🛠️ macOS-Specific Troubleshooting

### **Common macOS Issues**

#### **Connection Problems**
- **Firewall Blocking**: Check macOS Application Firewall settings
  ```bash
  sudo /usr/libexec/ApplicationFirewall/socketfilterfw --listapps
  ```
- **Network Location**: Verify correct network location is active
  ```bash
  networksetup -getcurrentlocation
  networksetup -listlocations
  ```
- **DNS Issues**: Check DNS configuration and resolution
  ```bash
  scutil --dns
  nslookup google.com
  ```

#### **Authentication Issues**
- **SSH Configuration**: Check SSH daemon configuration
  ```bash
  sudo launchctl list | grep ssh
  cat /etc/ssh/sshd_config
  ```
- **Keychain Access**: Verify SSH keys in Keychain
  ```bash
  ssh-add -l
  security find-generic-password -s "SSH"
  ```
- **Permissions**: Check SSH key file permissions
  ```bash
  ls -la ~/.ssh/
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/id_rsa
  ```

#### **Performance Issues**
- **Thermal Throttling**: Check for thermal throttling
  ```bash
  pmset -g thermlog
  powermetrics -n 1 -i 1000 --samplers cpu_power,gpu_power
  ```
- **Memory Pressure**: Monitor memory usage and pressure
  ```bash
  memory_pressure
  vm_stat
  ```
- **Background Processes**: Identify resource-intensive processes
  ```bash
  top -o cpu
  Activity Monitor.app
  ```

#### **Docker Issues**
- **Docker Desktop**: Check Docker Desktop status
  ```bash
  docker version
  docker system info
  ```
- **Resource Limits**: Adjust Docker Desktop resource allocation
  - Open Docker Desktop → Preferences → Resources
  - Adjust CPU, Memory, and Disk limits

### **macOS System Monitoring Tools**

#### **Built-in Monitoring Commands**
```bash
# System information
system_profiler SPHardwareDataType
sysctl -a | grep hw
uname -a

# Process monitoring
ps aux
top -o cpu
lsof -i

# Network monitoring
netstat -rn
ifconfig
networksetup -listallhardwareports

# System resources
df -h
du -sh /*
iostat 1
```

## 🔒 macOS Security Features

### **Enhanced Security Monitoring**
- **Gatekeeper Integration**: Application security and code signing verification
- **System Integrity Protection**: SIP status monitoring and compliance
- **FileVault Integration**: Disk encryption status and key management
- **Secure Boot**: T2/Apple Silicon secure boot status monitoring

### **Credential Security**
- **Keychain Services**: Secure credential storage via macOS Keychain
- **Touch ID/Face ID**: Biometric authentication for sensitive operations
- **Certificate Management**: macOS Certificate Assistant integration
- **Secure Enclave**: Hardware security module integration (T2/Apple Silicon)

## 📈 Performance Optimization for macOS

### **macOS-Specific Optimizations**
- **Energy Saver**: Automatic power management optimization for mining
- **App Nap**: Intelligent app suspension for background efficiency
- **Compressed Memory**: macOS memory compression optimization
- **Metal Performance**: GPU acceleration via Metal framework

### **Monitoring Efficiency**
- **Grand Central Dispatch**: Efficient concurrent monitoring via GCD
- **Core Foundation**: Low-level system monitoring APIs
- **IOKit**: Hardware monitoring via IOKit framework
- **Activity Monitor**: Integration with macOS Activity Monitor

## 🆘 macOS Support Resources

### **macOS-Specific Help**
- **Console App**: Reading system logs and crash reports
- **Activity Monitor**: System resource monitoring and analysis
- **Network Utility**: Network diagnostics and troubleshooting
- **System Information**: Comprehensive hardware and software information

### **Common macOS Commands**
```bash
# Check SSH service
sudo launchctl list | grep ssh
sudo systemsetup -getremotelogin

# Test network connectivity
ping -c 4 mining-machine-ip
nc -zv mining-machine-ip 22

# Check Docker
docker version
docker ps
open -a Docker

# Monitor system performance
top -o cpu
vm_stat 1
iostat 1
```

## 🔄 Upgrading from Previous Versions

### **From v2.0.2 on macOS**
- **Application Replacement**: Replace app in Applications folder
- **Preferences Migration**: macOS preferences automatically migrated
- **Keychain Preservation**: Keychain entries preserved during upgrade
- **Launch Agents**: macOS launch agents updated automatically

### **macOS-Specific Migration Notes**
- **Code Signing**: New version maintains valid code signature
- **Notarization**: Updated notarization for enhanced security
- **Permissions**: Application permissions preserved during upgrade
- **Spotlight Index**: Spotlight metadata updated automatically

## 🍎 Apple Silicon vs Intel

### **Apple Silicon (M1/M2/M3) Optimizations**
- **Native ARM64**: Optimized native ARM64 build for best performance
- **Unified Memory**: Efficient memory usage with unified memory architecture
- **Neural Engine**: Potential ML acceleration for monitoring algorithms
- **Power Efficiency**: Enhanced battery life and thermal management

### **Intel Mac Support**
- **x86_64 Native**: Native Intel build for optimal compatibility
- **Rosetta 2**: Automatic translation layer if needed
- **Legacy Support**: Full support for older Intel Mac systems
- **Performance**: Optimized for Intel architecture and features

## 🌐 Universal Binary

The macOS version includes Universal Binary support:
- **Native Performance**: Runs natively on both Intel and Apple Silicon
- **Automatic Selection**: macOS automatically selects the correct architecture
- **Optimized Code**: Architecture-specific optimizations for both platforms
- **Seamless Experience**: Identical features and performance across architectures

---

**Polaris Node Manager v2.0.3 for macOS** provides the most comprehensive mining management experience with deep macOS system integration. Take advantage of native macOS frameworks and security features for optimal mining performance and monitoring.

For macOS-specific support, use Console.app to view system logs and Activity Monitor for performance analysis. The application integrates seamlessly with macOS security and monitoring frameworks. 