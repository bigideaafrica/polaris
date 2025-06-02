# Polaris Node Manager v2.0.0

Welcome to **Polaris Node Manager v2** - a powerful, modern application for managing multiple mining machines with advanced validation and real-time monitoring capabilities.

## 🌟 Overview

Polaris Node Manager v2 represents a complete evolution from v1, introducing multi-machine management, automated validation systems, and a modern React-based interface. Built with scalability and user experience in mind, v2 enables you to efficiently manage multiple mining rigs under a single unified identifier.

## ✨ Key Features

### 🔧 Multi-Machine Management
- **Unified UID System**: Register and manage multiple mining rigs under a single user identifier
- **Centralized Control**: Monitor and control all your mining machines from one interface
- **Scalable Architecture**: Add unlimited mining machines to your network
- **Machine Table View**: Comprehensive view of all mining rigs with specifications, IP addresses, ports, and status
- **Bulk Operations**: Refresh all machines or stop all operations with single-click actions

### 🌐 Bittensor Network Integration
- **Subnet Registration**: Seamless integration with Bittensor subnet 49 (polariscloud.ai)
- **UID Management**: Automatic UID assignment and tracking (e.g., UID 123)
- **Network Status**: Real-time subnet registration status and connectivity monitoring
- **Wallet Integration**: Register and manage cryptocurrency wallets for mining operations

### 🛡️ Advanced Validation System
- **Automated Server Authentication**: Verify SSH access and connectivity automatically
- **Performance Benchmarking**: Built-in CPU and GPU performance scoring
- **System Verification**: Comprehensive hardware detection and validation
- **Proof of Work**: Real-time system benchmarking with performance scoring

### 📊 Real-Time Monitoring & Logging
- **Live Status Tracking**: Monitor all connected mining machines in real-time
- **Activity Logging**: Detailed logging of mining operations and system events
- **API Response Monitoring**: Track all API communications and server responses
- **Performance Metrics**: Track CPU scores, GPU scores, and total performance ratings
- **Network Monitoring**: Monitor connection status and response times
- **Session Management**: Track session expiration and user authentication status

### 🎛️ Machine Management Interface
- **Detailed Machine Specs**: View CPU/GPU information, RAM, storage, and IP configurations
- **Status Indicators**: Real-time status updates (Connected, Pending, Rejected)
- **Validation Status**: Track verification status for each machine
- **Individual Actions**: Configure, delete, or manage individual machines
- **Search & Filter**: Search by miner username and filter by status

### 🎨 Modern User Interface
- **React + Material-UI Joy**: Clean, responsive, and intuitive interface
- **Cross-Platform Design**: Consistent experience across Windows, macOS, and Linux
- **Real-Time Updates**: Live status indicators and progress tracking
- **Responsive Layout**: Optimized for different screen sizes and resolutions
- **Session Indicators**: User welcome messages and session expiration timers

### 🛠️ Support & Maintenance
- **Contact Support**: Built-in support contact system for technical assistance
- **Activity Logs**: Exportable logs for troubleshooting and analysis
- **Clear Logs**: Easy log management and cleanup functionality
- **User Management**: User session tracking and logout capabilities

### 🖥️ Enhanced Cross-Platform Support
- **Windows**: Native Windows application with installer and portable versions
- **Linux**: DEB/RPM packages and portable tarballs
- **MacOS**: DMG installer with Apple Silicon and Intel support

## 📥 Downloads

Choose the appropriate installer for your operating system:

### Windows
- [**Installer (Recommended)**](./windows/PolarisNodeManager-Setup.exe) - Full installation with shortcuts and auto-updates
- [Portable Version](./windows/PolarisNodeManager-Portable.zip) - No installation required

### Linux
- [**DEB Package**](./linux/polaris-node-manager_2.0.0_amd64.deb) - For Ubuntu/Debian
- [**RPM Package**](./linux/polaris-node-manager_2.0.0_x86_64.rpm) - For Fedora/RHEL/CentOS
- [Portable Tarball](./linux/polaris-node-manager-linux-x86_64.tar.gz) - Universal Linux

### MacOS
- [**DMG Installer**](./macos/PolarisNodeManager-2.0.0.dmg) - For macOS 10.15+
- [Portable App](./macos/PolarisNodeManager-Portable.zip) - Drag and drop installation

## 🚀 Quick Start

### 1. Installation

#### Windows
```powershell
# Download and run installer
Invoke-WebRequest -Uri "https://github.com/BANADDA/polaris_distributions/raw/main/v2/windows/PolarisNodeManager-Setup.exe" -OutFile "PolarisNodeManager-Setup.exe"
Start-Process -FilePath ".\PolarisNodeManager-Setup.exe"
```

#### Linux (Ubuntu/Debian)
```bash
# Download and install DEB package
wget "https://github.com/BANADDA/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_amd64.deb"
sudo dpkg -i polaris-node-manager_2.0.0_amd64.deb
sudo apt-get install -f  # Install dependencies
```

#### Linux (Fedora/RHEL/CentOS)
```bash
# Download and install RPM package
wget "https://github.com/BANADDA/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_x86_64.rpm"
sudo rpm -i polaris-node-manager_2.0.0_x86_64.rpm
```

#### MacOS
```bash
# Download DMG file
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v2/macos/PolarisNodeManager-2.0.0.dmg" -o "PolarisNodeManager-2.0.0.dmg"
# Open DMG and drag to Applications folder
```

### 2. Adding Your First Mining Machine

1. **Launch** Polaris Node Manager v2
2. **Click** "Add Mining Machine" button
3. **Follow** the automated setup process:
   - **Connect**: Enter machine connection details
   - **System**: Automatic system detection and configuration
   - **Validation**: Automated server authentication and performance testing
   - **Register**: Complete machine registration under your UID

### 3. Validation Process

The new validation system includes:

- **Server Authentication**: 
  - SSH access verification
  - Connectivity testing
  - Authentication success confirmation
  - Response time measurement

- **Proof of Work**:
  - CPU performance benchmarking
  - GPU performance scoring (if available)
  - Total system performance rating
  - Hardware specification detection

## 📋 System Requirements

### Minimum Requirements
- **RAM**: 4GB (8GB recommended for managing 5+ machines)
- **Storage**: 500MB free disk space
- **Network**: Stable internet connection (minimum 10 Mbps)
- **CPU**: Dual-core processor (Quad-core recommended)

### Recommended for Optimal Performance
- **RAM**: 16GB+ for managing 10+ mining machines
- **Storage**: 2GB+ free disk space (for logs and cache)
- **Network**: High-speed connection (100+ Mbps) for real-time monitoring
- **CPU**: Multi-core processor (6+ cores for heavy workloads)

### Platform-Specific Requirements

#### Windows
- Windows 10 build 1903+ or Windows 11
- .NET 6.0 Runtime (included in installer)
- Windows PowerShell 5.1 or PowerShell 7+
- Windows Defender exclusion recommended

#### Linux
- Modern Linux distribution (kernel 4.18+)
- systemd support
- GTK3+ libraries
- OpenSSL 1.1.1 or newer

#### MacOS
- macOS 10.15 (Catalina) or later
- Apple Silicon (M1/M2) and Intel processors supported
- Xcode command line tools (for some features)

## 🔧 Features Deep Dive

### Multi-Machine Management

**Register Multiple Machines Under One UID**:
- All your mining machines share a single user identifier
- Centralized management and monitoring
- Simplified authentication and access control
- Unified reporting and analytics

**Machine Status Indicators**:
- 🟢 **Verified**: Machine is online and mining successfully
- 🟡 **Pending**: Machine is connecting or initializing
- 🔴 **Rejected**: Machine has encountered an error or is offline

### Self-Validation System

**Automated Setup Process**:
1. **Connection Test**: Verify network connectivity and SSH access
2. **System Discovery**: Detect hardware specifications and capabilities
3. **Performance Benchmark**: Run CPU and GPU performance tests
4. **Validation**: Confirm all systems are ready for mining operations

**Performance Scoring**:
- **CPU Score**: Single and multi-core performance rating
- **GPU Score**: Graphics processing performance (if available)
- **Total Score**: Combined system performance rating
- **Benchmark Results**: Detailed performance metrics and comparisons

### Real-Time Monitoring

**Live Dashboard**:
- Real-time status updates for all connected machines
- Performance metrics and health indicators
- Network latency and connection quality monitoring
- Resource utilization tracking

**Activity Logging**:
- Comprehensive logging of all mining operations
- System events and error tracking
- Performance history and trends
- Exportable logs for analysis

## 🆕 What's New from v1

| Feature | v1.0.0 | v2.0.0 |
|---------|--------|--------|
| **Machine Management** | Single machine only | Multiple machines under one UID |
| **User Interface** | Basic desktop GUI | Modern React + Material-UI Joy |
| **Validation** | Manual configuration | Automated self-validation system |
| **Monitoring** | Basic status display | Real-time monitoring + activity logs |
| **Performance Testing** | None | Built-in CPU/GPU benchmarking |
| **Cross-Platform** | Windows + Linux | Windows + Linux + MacOS |
| **Authentication** | Simple login | Advanced SSH + server validation |
| **Scalability** | Single node | Unlimited node management |

## 🛠️ Advanced Configuration

### Environment Variables
```bash
# Set custom configuration directory
export POLARIS_CONFIG_DIR="/path/to/config"

# Enable debug logging
export POLARIS_DEBUG=true

# Set custom cache directory
export POLARIS_CACHE_DIR="/path/to/cache"
```

### Configuration Files
- **Windows**: `%APPDATA%\PolarisNodeManager\config.json`
- **Linux**: `~/.config/polaris-node-manager/config.json`
- **MacOS**: `~/Library/Application Support/PolarisNodeManager/config.json`

## 🐛 Troubleshooting

### Common Issues

**Connection Problems**:
- Verify SSH access and credentials
- Check firewall settings
- Ensure network connectivity

**Performance Issues**:
- Close unnecessary applications
- Check available RAM and CPU resources
- Update graphics drivers for GPU scoring

**Installation Issues**:
- Run installer as administrator (Windows)
- Check file permissions (Linux/MacOS)
- Disable antivirus temporarily during installation

### Support

For technical support and bug reports:
- 📧 Email: support@polarisnode.com
- 💬 Discord: [Join our community](https://discord.gg/polaris)
- 📖 Documentation: [Full docs](https://docs.polarisnode.com)
- 🐛 Issues: [GitHub Issues](https://github.com/BANADDA/polaris_distributions/issues)

## 📈 Performance Optimization

### For Managing Multiple Machines
- Allocate sufficient RAM (8GB+ recommended)
- Use SSD storage for better I/O performance
- Ensure stable network connection
- Close unnecessary background applications

### For Better Validation Performance
- Update system drivers (especially GPU)
- Ensure adequate cooling for accurate benchmarks
- Close resource-intensive applications during validation
- Use wired network connection when possible

## 🔄 Migration from v1

**Automatic Migration**:
- v2 can import v1 configurations automatically
- Existing machine credentials will be preserved
- Activity logs from v1 can be imported

**Manual Migration Steps**:
1. Export your v1 configuration
2. Install Polaris Node Manager v2
3. Import configuration during first launch
4. Re-validate machines with new system

## 📊 Version History

### v2.0.0 (Current Release)
- ✅ Multi-machine management with unified UID
- ✅ Automated self-validation system
- ✅ Modern React + Material-UI interface
- ✅ Real-time monitoring and activity logging
- ✅ Enhanced cross-platform support (Windows/Linux/MacOS)
- ✅ Performance benchmarking and scoring
- ✅ Advanced SSH authentication and connectivity testing

### Coming in v2.1.0
- 📊 Advanced analytics dashboard
- 📈 Historical performance tracking
- 🔔 Advanced notification system
- 🌐 Web-based remote management
- 📱 Mobile companion app

## 📄 License

Polaris Node Manager v2 is distributed under the [MIT License](https://opensource.org/licenses/MIT).

---

**Ready to manage your mining empire?** Download Polaris Node Manager v2 today and experience the future of multi-machine mining management! 🚀
