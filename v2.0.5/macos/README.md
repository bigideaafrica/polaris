# Polaris Node Manager v2.0.5 - macOS Distribution

**Polaris Node Manager v2.0.5** for macOS delivers critical infrastructure updates with enhanced server key management and refined endpoint configurations, ensuring optimal connectivity and improved mining performance.

## 🍎 macOS Distribution

This directory contains the macOS builds of Polaris Node Manager v2.0.5, optimized for both Apple Silicon (M1/M2) and Intel-based Macs.

### Available Files

- **macos-latest-build.zip** - Universal macOS application bundle supporting both Apple Silicon and Intel processors

## 🔧 What's New in v2.0.5

- **Updated Server Keys**: Enhanced server key infrastructure with improved authentication protocols
- **Endpoint Optimization**: Refined endpoint configurations for better connectivity and reduced latency
- **Infrastructure Hardening**: Server-side improvements for enhanced stability and performance
- **Connection Reliability**: Improved connection management with better failover mechanisms
- **Performance Optimizations**: Backend optimizations for faster response times and reduced overhead

## 📥 Installation

### System Requirements

- **OS**: macOS 11.0 (Big Sur) or later
- **Architecture**: Universal Binary (Apple Silicon M1/M2 and Intel x86_64)
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 1GB free disk space
- **Network**: Stable internet connection
- **Permissions**: Administrative privileges may be required

### Quick Installation

```bash
# Download the build
curl -L -o macos-latest-build.zip ./macos-latest-build.zip

# Extract the package
unzip macos-latest-build.zip

# Navigate to extracted directory
cd polaris-node-manager-macos-v2.0.5

# Open the application
open "Polaris Node Manager.app"
```

### Alternative Installation Methods

#### Method 1: Direct Download and Install
```bash
# Download from GitHub releases
curl -L -o polaris-macos-v2.0.5.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.5/macos-latest-build.zip

# Extract to Applications folder
unzip polaris-macos-v2.0.5.zip
sudo mv "Polaris Node Manager.app" /Applications/

# Launch from Applications
open /Applications/"Polaris Node Manager.app"
```

#### Method 2: Drag and Drop Installation
1. Download and extract `macos-latest-build.zip`
2. Open Finder and navigate to the extracted folder
3. Drag "Polaris Node Manager.app" to your Applications folder
4. Launch from Applications or Spotlight

## 🚀 Quick Start

1. **Download**: Get `macos-latest-build.zip` from this directory
2. **Extract**: Unzip the package to reveal the app bundle
3. **Install**: Move to Applications folder (optional but recommended)
4. **Authorize**: Allow the app to run when prompted by Gatekeeper
5. **Setup**: Follow the in-app setup wizard to configure your mining machines

## 🔒 Security and Gatekeeper

### First Launch Authorization

When launching for the first time, macOS Gatekeeper may block the application:

1. **If you see "Cannot be opened"**:
   - Go to System Preferences → Security & Privacy
   - Click "Open Anyway" next to the Polaris Node Manager message
   - Alternatively, right-click the app and select "Open"

2. **For macOS Monterey and later**:
   ```bash
   # Remove quarantine attribute (if needed)
   xattr -d com.apple.quarantine "/Applications/Polaris Node Manager.app"
   ```

### Code Signing and Notarization

This application is:
- ✅ **Signed**: With valid Apple Developer ID
- ✅ **Notarized**: Approved by Apple's notarization service
- ✅ **Hardened Runtime**: Enhanced security features enabled

## 🍎 macOS-Specific Features

### Native Integration
- **Menu Bar Integration**: System tray icon for quick access
- **Notifications**: Native macOS notifications for mining status
- **Keychain Integration**: Secure credential storage in macOS Keychain
- **Spotlight Search**: Find and launch via Spotlight
- **Mission Control**: Full support for macOS window management

### Apple Silicon Optimization
- **Native M1/M2 Support**: Optimized for Apple Silicon processors
- **Energy Efficiency**: Reduced power consumption on Apple Silicon
- **Performance**: Up to 2x faster performance on M1/M2 compared to Intel
- **Universal Binary**: Single app works on both architectures

## 📋 Prerequisites

### Required System Components
```bash
# Verify macOS version
sw_vers

# Check architecture
uname -m
# Output: arm64 (Apple Silicon) or x86_64 (Intel)

# Ensure Xcode Command Line Tools (if needed for advanced features)
xcode-select --install
```

### Network Configuration
```bash
# Verify HTTPS connectivity
curl -I https://polariscloud.ai

# Check DNS resolution
nslookup polariscloud.ai

# Test TLS 1.3 support
openssl s_client -connect polariscloud.ai:443 -tls1_3
```

## 🛠️ Troubleshooting

### Common Issues

#### App Won't Launch
```bash
# Check if app is damaged
spctl -a -v "/Applications/Polaris Node Manager.app"

# Remove quarantine if needed
xattr -d com.apple.quarantine "/Applications/Polaris Node Manager.app"

# Check console for errors
log show --predicate 'subsystem contains "com.polariscloud"' --last 1h
```

#### Permission Issues
```bash
# Grant necessary permissions in System Preferences
# Go to: System Preferences → Security & Privacy → Privacy
# Add Polaris Node Manager to:
# - Full Disk Access (if managing files)
# - Network (for mining operations)
# - Notifications (for status alerts)
```

#### Performance Issues on Intel Macs
```bash
# Verify app is running natively (not under Rosetta)
ps aux | grep -i polaris

# Force native execution
arch -arm64 open "/Applications/Polaris Node Manager.app"  # M1/M2
arch -x86_64 open "/Applications/Polaris Node Manager.app"  # Intel
```

#### Network Connectivity Issues
```bash
# Check firewall settings
sudo pfctl -s rules | grep -i polaris

# Test with network utility
networkQuality

# Verify certificate trust
security verify-cert -c /path/to/certificate.pem
```

### Advanced Troubleshooting

#### Reset Application Preferences
```bash
# Remove application preferences
rm -rf ~/Library/Preferences/com.polariscloud.polaris-node-manager.plist
rm -rf ~/Library/Application\ Support/PolarisNodeManager/

# Clear application caches
rm -rf ~/Library/Caches/com.polariscloud.polaris-node-manager/
```

#### Debug Mode
```bash
# Launch with debug logging
/Applications/"Polaris Node Manager.app"/Contents/MacOS/"Polaris Node Manager" --debug

# View application logs
log show --predicate 'subsystem contains "polariscloud"' --last 30m
```

## 🔒 Security Best Practices

### Keychain Management
- Credentials are stored securely in macOS Keychain
- Use strong passwords for keychain access
- Enable two-factor authentication where supported

### Network Security
```bash
# Verify secure connections
lsof -i -P | grep polaris

# Check certificate validity
openssl s_client -connect polariscloud.ai:443 -servername polariscloud.ai
```

## 📊 Performance Optimization

### For Apple Silicon (M1/M2)
- **Memory**: 8GB unified memory recommended
- **Storage**: SSD with at least 100GB free space
- **Network**: Wi-Fi 6 or Ethernet for best performance
- **Power**: Keep connected to power for sustained performance

### For Intel Macs
- **Memory**: 16GB RAM recommended for heavy workloads
- **Cooling**: Ensure adequate cooling for sustained performance
- **Network**: Wired connection preferred for stability
- **CPU**: Recent Intel processors (8th gen or newer) recommended

### System Optimization
```bash
# Check system resources
top -l 1 -s 0 | grep PhysMem
df -h

# Monitor network usage
nettop -P

# Check thermal state (Apple Silicon)
pmset -g thermstate
```

## 📞 Support

For macOS-specific issues:

- **General Support**: support@polariscloud.ai
- **macOS Issues**: macos-support@polariscloud.ai
- **GitHub Issues**: [Report macOS-specific bugs](https://github.com/bigideaafrica/polaris_distributions/issues)

When reporting issues, include:
- macOS version (`sw_vers`)
- Hardware type (`system_profiler SPHardwareDataType`)
- Console logs (`log show --last 1h`)
- Network configuration details

## 📄 Additional Information

- **License**: MIT License
- **Version**: 2.0.5
- **Build Date**: January 2024
- **Architecture**: Universal Binary (arm64 + x86_64)
- **Minimum macOS**: 11.0 (Big Sur)
- **Bundle ID**: com.polariscloud.polaris-node-manager

## 🔄 Auto-Updates

Polaris Node Manager includes built-in auto-update functionality:
- Automatic check for updates on startup
- Secure download and verification of updates
- Seamless installation with user consent
- Rollback capability if issues occur

---

**Note**: This macOS distribution includes all the infrastructure improvements from v2.0.5, optimized specifically for macOS environments with native Apple Silicon support. For the complete feature list and detailed documentation, see the main [v2.0.5 README](../README.md). 