# Polaris Node Manager v2.0.4 - macOS

**Security-Enhanced Release for macOS Big Sur and Later**

This release introduces critical security enhancements including updated server public keys, endpoint security hardening, and comprehensive TLS 1.3 implementation optimized for both Intel and Apple Silicon Macs.

## 🔒 Security Enhancements in v2.0.4

### macOS-Specific Security Features
- **Keychain Integration**: Seamless integration with macOS Keychain Services
- **Code Signing**: Notarized application with Apple Developer ID signature
- **Gatekeeper Compatibility**: Full compatibility with macOS Gatekeeper security
- **Sandbox Support**: Enhanced App Sandbox for improved security isolation
- **Touch ID/Face ID Integration**: Biometric authentication support where available

### Updated Security Components
- **RSA-4096 Server Keys**: Enhanced cryptographic protection
- **Native TLS 1.3**: Utilizes macOS native Secure Transport for TLS 1.3
- **Certificate Pinning**: Automatic certificate validation and pinning
- **Encrypted Data Storage**: AES-256-GCM encryption using macOS Security Framework
- **System Integrity Protection**: Full SIP compliance

## Download Information

### File Details
- **Filename**: `polaris-node-manager-macos-v2.0.4.zip`
- **Size**: ~905MB (increased from v2.0.3 due to security libraries and universal binary)
- **Format**: ZIP archive containing Universal macOS application
- **Architecture**: Universal Binary (Intel x64 + Apple Silicon ARM64)
- **Minimum macOS**: macOS 11.0 Big Sur

### Checksum Verification
```bash
# Verify file integrity
shasum -a 256 polaris-node-manager-macos-v2.0.4.zip
# Expected: [SHA256 hash will be provided with release]

# Verify application bundle integrity
codesign -dv --verbose=4 "Polaris Node Manager.app"
```

## System Requirements

### Minimum Requirements (Updated for v2.0.4)
- **OS**: macOS 11.0 Big Sur or later (macOS 13.0 Ventura recommended)
- **Processor**: Intel Core i5 or Apple M1/M2 (Universal Binary)
- **RAM**: 4GB minimum (8GB recommended for secure multi-machine management)
- **Storage**: 1GB free disk space (increased for security libraries)
- **Network**: TLS 1.3 capable internet connection
- **Permissions**: Administrator privileges for initial setup

### Security Requirements
- **Gatekeeper**: macOS Gatekeeper enabled (default)
- **System Integrity Protection**: SIP enabled (recommended)
- **Keychain Access**: Available for secure credential storage
- **Network Extensions**: Allowed in System Preferences
- **Firewall**: macOS Firewall configuration access

### Hardware Security Features (Optional)
- **Touch ID**: For biometric authentication (MacBook Pro/Air, iMac Pro)
- **Face ID**: For biometric authentication (newer MacBook models)
- **Secure Enclave**: Hardware security module (T2/M1/M2 chips)
- **Hardware Encryption**: FileVault integration for enhanced security

## Installation Methods

### Method 1: Direct Download (Recommended)
```bash
# Download the release
curl -L -o polaris-v2.0.4-macos.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-macos-v2.0.4.zip

# Extract the archive
unzip polaris-v2.0.4-macos.zip

# Navigate to extracted directory
cd polaris-node-manager-macos-v2.0.4

# Launch the application
open "Polaris Node Manager.app"
```

### Method 2: Homebrew (Community Maintained)
```bash
# Add Polaris tap (if available)
brew tap bigideaafrica/polaris

# Install Polaris Node Manager
brew install --cask polaris-node-manager

# Launch application
open -a "Polaris Node Manager"
```

### Method 3: Manual Installation
1. Visit [Releases Page](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.4)
2. Download `polaris-node-manager-macos-v2.0.4.zip`
3. Double-click the downloaded ZIP file to extract
4. Drag `Polaris Node Manager.app` to Applications folder
5. Launch from Applications or Spotlight

## macOS-Specific Security Configuration

### Gatekeeper and Code Signing
The application is properly code-signed and notarized:

```bash
# Verify code signature
codesign -dv --verbose=4 "Polaris Node Manager.app"

# Check notarization status
spctl -a -vvv -t install "Polaris Node Manager.app"

# Expected output should show: accepted
# source=Notarized Developer ID
```

### First Launch Security Dialog
When first launching the application, macOS may show security dialogs:

**If you see "macOS cannot verify the developer":**
1. Open System Preferences → Security & Privacy
2. Click "Allow Anyway" next to the blocked application
3. Re-launch the application
4. Click "Open" when prompted

**Alternative method:**
1. Right-click the application in Finder
2. Select "Open" from context menu
3. Click "Open" in the security dialog

### Keychain Integration
The application integrates with macOS Keychain:

```bash
# View Polaris keychain entries
security find-internet-password -s "polariscloud.ai"

# List Polaris certificates in keychain
security find-certificate -a -c "Polaris Node Manager"
```

### Privacy Permissions
The application may request the following permissions:
- **Network Connections**: For mining machine communication
- **Keychain Access**: For secure credential storage
- **Notifications**: For status updates and alerts
- **Files and Folders**: For configuration file access

## Running the Application

### Application Bundle Structure
```
Polaris Node Manager.app/
├── Contents/
│   ├── Info.plist           # Application metadata
│   ├── MacOS/               # Executable binaries
│   │   └── Polaris Node Manager
│   ├── Resources/           # Application resources
│   │   ├── icon.icns        # Application icon
│   │   ├── certificates/    # Certificate bundle
│   │   └── security/        # Security configurations
│   └── _CodeSignature/      # Code signing information
```

### Application Data Directories
```bash
# Main configuration directory
~/Library/Application Support/Polaris Node Manager/
├── config.json             # Main configuration (encrypted)
├── certificates/           # Certificate cache
├── logs/                   # Application logs
├── machines/               # Machine configurations
└── security/              # Security keys and tokens

# Preferences (managed by macOS)
~/Library/Preferences/com.polariscloud.nodemanager.plist

# Caches
~/Library/Caches/com.polariscloud.nodemanager/

# Keychain entries (managed by macOS Keychain)
# Accessible via Keychain Access.app
```

## macOS-Specific Features

### Native macOS Integration
- **Menu Bar Integration**: Native macOS menu bar with application menus
- **Dock Integration**: Proper Dock icon with badge notifications
- **Notification Center**: Native macOS notifications for status updates
- **Spotlight Search**: Application indexed for Spotlight search
- **Quick Look**: Preview support for configuration files

### Apple Silicon Optimizations
- **Native ARM64**: Optimized for Apple M1/M2 processors
- **Energy Efficiency**: Reduced power consumption on Apple Silicon
- **Metal Performance**: GPU acceleration using Metal framework
- **Neural Engine**: ML acceleration where applicable

### Security Framework Integration
- **Secure Enclave**: Hardware-based key storage (T2/M1/M2 chips)
- **CommonCrypto**: Native macOS cryptographic framework
- **Network Extension**: Secure network communication framework
- **App Transport Security**: Enhanced network security compliance

## Troubleshooting

### Common Issues and Solutions

#### 1. "App is damaged and can't be opened"
**Symptoms**: macOS prevents application from launching
**Solutions**:
```bash
# Remove quarantine attribute
xattr -d com.apple.quarantine "Polaris Node Manager.app"

# Alternative: Clear all extended attributes
xattr -c "Polaris Node Manager.app"

# Verify the application afterwards
spctl -a -vvv -t install "Polaris Node Manager.app"
```

#### 2. "Developer cannot be verified"
**Symptoms**: Gatekeeper blocks application launch
**Solutions**:
1. **System Preferences Method**:
   - Open System Preferences → Security & Privacy
   - Click "Open Anyway" button
   - Re-launch application

2. **Command Line Method**:
   ```bash
   # Temporarily disable Gatekeeper (not recommended)
   sudo spctl --master-disable
   # Launch application
   # Re-enable Gatekeeper
   sudo spctl --master-enable
   ```

#### 3. "Certificate validation failed"
**Symptoms**: Network connection errors, SSL failures
**Solutions**:
```bash
# Update macOS system certificates
sudo /usr/sbin/certificates update

# Check system date/time (common cause)
sudo sntp -sS time.apple.com

# Reset Keychain if needed
# Open Keychain Access → Keychain Access menu → Reset My Default Keychain
```

#### 4. "Permission denied" errors
**Symptoms**: Cannot access configuration files
**Solutions**:
```bash
# Check application permissions
ls -la ~/Library/Application\ Support/Polaris\ Node\ Manager/

# Reset permissions if needed
chmod -R 700 ~/Library/Application\ Support/Polaris\ Node\ Manager/

# Clear application cache
rm -rf ~/Library/Caches/com.polariscloud.nodemanager/
```

#### 5. "Network connectivity issues"
**Symptoms**: Cannot connect to Polaris servers
**Solutions**:
```bash
# Test network connectivity
ping polariscloud.ai

# Check DNS resolution
dig polariscloud.ai

# Test TLS 1.3 connectivity
openssl s_client -connect polariscloud.ai:443 -tls1_3

# Check macOS Firewall settings
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
```

### System Information for Support
```bash
#!/bin/bash
# Generate system information for support

echo "=== System Information ==="
echo "macOS Version: $(sw_vers -productVersion)"
echo "Build Number: $(sw_vers -buildVersion)"
echo "Hardware: $(system_profiler SPHardwareDataType | grep "Model Name\|Chip\|Processor Name" | head -2)"

echo "=== Security Information ==="
echo "Gatekeeper Status: $(spctl --status)"
echo "SIP Status: $(csrutil status)"
echo "FileVault Status: $(fdesetup status)"

echo "=== Network Information ==="
echo "Active Network Service: $(networksetup -listallhardwareports | grep -A1 "Wi-Fi\|Ethernet" | grep "Device" | head -1)"
echo "DNS Servers: $(networksetup -getdnsservers Wi-Fi 2>/dev/null || networksetup -getdnsservers Ethernet)"

echo "=== Application Information ==="
echo "Code Signature: $(codesign -dv "Polaris Node Manager.app" 2>&1)"
echo "Quarantine Status: $(xattr -l "Polaris Node Manager.app" | grep quarantine || echo "Not quarantined")"

echo "=== Certificate Information ==="
echo "System Certificates: $(security list-keychains | wc -l) keychains available"
echo "Polaris Certificates: $(security find-certificate -a -c "Polaris" | grep "cert" | wc -l) found"
```

## Performance Optimization

### macOS-Specific Optimizations
- **Grand Central Dispatch**: Utilizes GCD for optimal threading
- **Core Foundation**: Native macOS frameworks for system integration
- **Metal Performance Shaders**: GPU acceleration for cryptographic operations
- **Network Framework**: Optimized networking using macOS Network framework

### Apple Silicon Performance
- **Native ARM64**: Full Apple Silicon optimization
- **Unified Memory**: Efficient memory usage on M1/M2 systems
- **Energy Efficiency**: Power-optimized for battery life
- **Thermal Management**: Intelligent thermal throttling

### Resource Usage
- **Memory**: ~95MB base usage (Intel), ~75MB (Apple Silicon)
- **CPU**: <1% idle usage, optimized for efficiency cores
- **Energy**: Minimal impact on battery life
- **Storage**: Efficient caching with automatic cleanup

## Advanced Security Configuration

### Enterprise Security Features
```bash
# Configuration Profile deployment (via MDM)
# Sample security configuration profile
sudo profiles install -path /path/to/polaris-security-profile.mobileconfig

# Certificate deployment
security add-certificates -k /Library/Keychains/System.keychain polaris-ca.crt

# Firewall rule for enterprise networks
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add "Polaris Node Manager"
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp "Polaris Node Manager"
```

### FileVault Integration
```bash
# Check FileVault status
fdesetup status

# Enable FileVault for enhanced security (requires restart)
sudo fdesetup enable

# Verify encryption status
diskutil cs list
```

## Automation and Scripting

### AppleScript Integration
```applescript
-- Launch Polaris Node Manager
tell application "Polaris Node Manager"
    activate
end tell

-- Check if application is running
tell application "System Events"
    if (name of processes) contains "Polaris Node Manager" then
        display notification "Polaris Node Manager is running" with title "Status Check"
    end if
end tell
```

### Shell Integration
```bash
# Create alias for easy launching
echo 'alias polaris="open -a \"Polaris Node Manager\""' >> ~/.zshrc

# Create function to check application status
polaris_status() {
    if pgrep -f "Polaris Node Manager" > /dev/null; then
        echo "✅ Polaris Node Manager is running"
    else
        echo "❌ Polaris Node Manager is not running"
    fi
}
```

## Development and Debugging

### Debug Mode
```bash
# Launch in debug mode
open "Polaris Node Manager.app" --args --debug

# View application logs
log stream --predicate 'processImagePath contains "Polaris"' --level debug

# Console application logs
open /Applications/Utilities/Console.app
# Filter for "Polaris Node Manager"
```

### Crash Reporting
```bash
# View crash reports
ls ~/Library/Logs/DiagnosticReports/Polaris*

# Submit crash report to developers
# Crash reports automatically include system information
# Submit via: crash-reports@polariscloud.ai
```

## Enterprise Deployment

### Mobile Device Management (MDM)
Deploy via MDM solutions like Jamf Pro, Kandji, or Microsoft Intune:

```xml
<!-- Sample deployment profile -->
<dict>
    <key>PayloadDisplayName</key>
    <string>Polaris Node Manager v2.0.4</string>
    <key>PayloadIdentifier</key>
    <string>com.polariscloud.nodemanager.deployment</string>
    <key>PayloadType</key>
    <string>Configuration</string>
    <key>PayloadVersion</key>
    <integer>1</integer>
</dict>
```

### Mass Deployment Script
```bash
#!/bin/bash
# Mass deployment script for enterprise environments

DOWNLOAD_URL="https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-macos-v2.0.4.zip"
INSTALL_DIR="/Applications"
TEMP_DIR="/tmp/polaris-install"

# Create temporary directory
mkdir -p "$TEMP_DIR"
cd "$TEMP_DIR"

# Download and verify
curl -L -o polaris-v2.0.4.zip "$DOWNLOAD_URL"
unzip polaris-v2.0.4.zip

# Install to Applications
sudo cp -R "Polaris Node Manager.app" "$INSTALL_DIR/"

# Set proper permissions
sudo chown -R root:admin "$INSTALL_DIR/Polaris Node Manager.app"
sudo chmod -R 755 "$INSTALL_DIR/Polaris Node Manager.app"

# Clean up
rm -rf "$TEMP_DIR"

echo "Polaris Node Manager v2.0.4 installed successfully"
```

## Support Information

### macOS-Specific Support Channels
- **macOS Issues**: macos-support@polariscloud.ai
- **Enterprise Support**: enterprise@polariscloud.ai
- **Security Issues**: security@polariscloud.ai

### Apple Developer Resources
- **Technical Support**: Available through Apple Developer Program
- **Code Signing Issues**: developer-support@polariscloud.ai
- **App Store Distribution**: (Planned for future releases)

## Version Information

- **Version**: 2.0.4
- **macOS Build**: 2.0.4-macos-universal
- **Architecture**: Universal Binary (Intel + Apple Silicon)
- **Security Level**: Enhanced
- **Support Until**: January 2025
- **Minimum macOS**: 11.0 Big Sur
- **Recommended macOS**: 13.0 Ventura or later

---

**Security Notice**: This version contains critical security updates. Upgrading from previous versions is strongly recommended. Always download from official sources and verify code signatures before installation.

**Apple Silicon Note**: This universal binary is optimized for both Intel and Apple Silicon Macs, providing native performance on all supported systems. 