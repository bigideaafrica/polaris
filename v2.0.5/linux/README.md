# Polaris Node Manager v2.0.5 - Linux Distribution

**Polaris Node Manager v2.0.5** for Linux delivers critical infrastructure updates with enhanced server key management and refined endpoint configurations, ensuring optimal connectivity and improved mining performance.

## 🐧 Linux Distribution

This directory contains the Linux builds of Polaris Node Manager v2.0.5, optimized for modern Linux distributions.

### Available Files

- **ubuntu-latest-build.zip** - Complete Linux application package with all dependencies

## 🔧 What's New in v2.0.5

- **Updated Server Keys**: Enhanced server key infrastructure with improved authentication protocols
- **Endpoint Optimization**: Refined endpoint configurations for better connectivity and reduced latency
- **Infrastructure Hardening**: Server-side improvements for enhanced stability and performance
- **Connection Reliability**: Improved connection management with better failover mechanisms
- **Performance Optimizations**: Backend optimizations for faster response times and reduced overhead

## 📥 Installation

### System Requirements

- **OS**: Ubuntu 20.04+, Fedora 35+, Debian 11+, or equivalent modern Linux distribution
- **Architecture**: x86_64 (64-bit)
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 800MB free disk space
- **Network**: Stable internet connection
- **Dependencies**: GTK3+ libraries, updated certificate store

### Quick Installation

```bash
# Download the build
wget ubuntu-latest-build.zip

# Extract the package
unzip ubuntu-latest-build.zip

# Navigate to extracted directory
cd polaris-node-manager-linux-v2.0.5

# Make executable
chmod +x polaris-node-manager-linux-v2.0.5.AppImage

# Run the application
./polaris-node-manager-linux-v2.0.5.AppImage
```

### Alternative Installation Methods

#### Method 1: Direct Download
```bash
# Download directly from GitHub releases
wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.5/ubuntu-latest-build.zip

# Extract and run
unzip ubuntu-latest-build.zip
cd polaris-node-manager-linux-v2.0.5
chmod +x *.AppImage
./polaris-node-manager-linux-v2.0.5.AppImage
```

#### Method 2: Desktop Integration
```bash
# Extract the AppImage
./polaris-node-manager-linux-v2.0.5.AppImage --appimage-extract

# Create desktop entry (optional)
cat > ~/.local/share/applications/polaris-node-manager.desktop << EOF
[Desktop Entry]
Type=Application
Name=Polaris Node Manager
Exec=$(pwd)/polaris-node-manager-linux-v2.0.5.AppImage
Icon=$(pwd)/squashfs-root/polaris-icon.png
Categories=Network;System;
EOF
```

## 🚀 Quick Start

1. **Download**: Get `ubuntu-latest-build.zip` from this directory
2. **Extract**: Unzip the package to your preferred location
3. **Execute**: Make the AppImage executable and run it
4. **Setup**: Follow the in-app setup wizard to configure your mining machines

## 🔧 Linux-Specific Features

### AppImage Benefits
- **Portable**: No installation required, runs on most Linux distributions
- **Self-contained**: All dependencies included
- **Secure**: Sandboxed execution environment
- **Easy updates**: Simply replace the AppImage file

### System Integration
- Desktop entry creation for easy access
- File association for Polaris configuration files
- System tray integration for background operation
- Automatic updates through built-in updater

## 📋 Prerequisites

### Required Packages (Most distributions)
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install libgtk-3-0 libglib2.0-0 libnss3 libatk-bridge2.0-0 libxss1 libgconf-2-4

# Fedora/RHEL
sudo dnf install gtk3 glib2 nss atk at-spi2-atk libXScrnSaver

# Arch Linux
sudo pacman -S gtk3 glib2 nss atk at-spi2-atk libxss
```

### SSL/TLS Support
```bash
# Update certificate store
sudo apt update && sudo apt install ca-certificates openssl

# Verify TLS 1.3 support
openssl s_client -connect polariscloud.ai:443 -tls1_3
```

## 🛠️ Troubleshooting

### Common Issues

#### AppImage Won't Run
```bash
# Make sure it's executable
chmod +x polaris-node-manager-linux-v2.0.5.AppImage

# Check for FUSE support
sudo apt install fuse libfuse2

# Run with verbose output for debugging
./polaris-node-manager-linux-v2.0.5.AppImage --appimage-debug
```

#### Missing Dependencies
```bash
# Install common dependencies
sudo apt install libgtk-3-0 libglib2.0-0 libnss3 libxss1

# For older distributions, you might need
sudo apt install libgconf-2-4 libxrandr2 libasound2-dev libpangocairo-1.0-0
```

#### Display Issues
```bash
# For Wayland users
export GDK_BACKEND=wayland

# For X11 fallback
export GDK_BACKEND=x11

# Force software rendering if needed
export LIBGL_ALWAYS_SOFTWARE=1
```

#### Permission Issues
```bash
# Ensure user has permissions for /tmp
ls -la /tmp

# Check AppImage permissions
ls -la polaris-node-manager-linux-v2.0.5.AppImage

# Run with strace for detailed debugging
strace -e trace=file ./polaris-node-manager-linux-v2.0.5.AppImage
```

## 🔒 Security Considerations

### File Verification
```bash
# Verify file integrity (if checksums provided)
sha256sum ubuntu-latest-build.zip

# Check AppImage signature (if available)
gpg --verify polaris-node-manager-linux-v2.0.5.AppImage.sig
```

### Firewall Configuration
```bash
# Allow HTTPS outbound connections
sudo ufw allow out 443/tcp

# Check firewall status
sudo ufw status
```

## 📊 Performance Optimization

### For Optimal Performance
- **CPU**: Multi-core processor recommended (4+ cores)
- **RAM**: 8GB+ for managing multiple mining machines
- **Storage**: SSD recommended for better I/O performance
- **Network**: Wired connection preferred for stability

### System Tuning
```bash
# Increase file descriptor limits if managing many machines
echo "* soft nofile 65536" | sudo tee -a /etc/security/limits.conf
echo "* hard nofile 65536" | sudo tee -a /etc/security/limits.conf

# For better network performance
echo 'net.core.rmem_max = 16777216' | sudo tee -a /etc/sysctl.conf
echo 'net.core.wmem_max = 16777216' | sudo tee -a /etc/sysctl.conf
```

## 📞 Support

For Linux-specific issues:

- **General Support**: support@polariscloud.ai
- **Linux Issues**: linux-support@polariscloud.ai
- **GitHub Issues**: [Report Linux-specific bugs](https://github.com/bigideaafrica/polaris_distributions/issues)

When reporting issues, include:
- Linux distribution and version (`lsb_release -a`)
- Desktop environment (`echo $XDG_CURRENT_DESKTOP`)
- Error output from terminal
- System specifications (`cat /proc/cpuinfo | grep "model name" | head -1`)

## 📄 Additional Information

- **License**: MIT License
- **Version**: 2.0.5
- **Build Date**: January 2024
- **Architecture**: x86_64
- **Minimum Kernel**: Linux 3.10+

---

**Note**: This Linux distribution includes all the infrastructure improvements from v2.0.5, optimized specifically for Linux environments. For the complete feature list and detailed documentation, see the main [v2.0.5 README](../README.md). 