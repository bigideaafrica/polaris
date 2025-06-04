# Polaris Node Manager v2.0.2 - macOS Installation Guide

**Enhanced Connection System & Security for macOS**

This guide covers the installation and usage of Polaris Node Manager v2.0.2 on macOS systems, featuring the new API-based connection system and enhanced SSH key management optimized for both Intel and Apple Silicon Macs.

## 🆕 macOS-Specific v2.0.2 Features

### Native macOS Integration
- **Universal Binary**: Full support for both Intel and Apple Silicon (M1/M2/M3) processors
- **Keychain Integration**: Secure storage of SSH keys using macOS Keychain
- **Spotlight Integration**: Application searchable through Spotlight
- **Native File Dialogs**: Enhanced file selection using native macOS file dialogs
- **Menu Bar Integration**: Optional menu bar operation for quick access

### Enhanced macOS Performance
- **API-Based Connections**: Optimized for macOS networking stack and security framework
- **Background Processing**: Better integration with macOS background app refresh
- **Memory Management**: Optimized memory usage following macOS best practices
- **Retina Display Support**: Enhanced UI scaling for high-resolution displays

## System Requirements

### Minimum Requirements
- **macOS**: 10.15 (Catalina) or later
  - macOS 10.15 Catalina
  - macOS 11.0 Big Sur
  - macOS 12.0 Monterey
  - macOS 13.0 Ventura
  - macOS 14.0 Sonoma (recommended)
- **Architecture**: Intel x86_64 or Apple Silicon (M1/M2/M3)
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 1GB free disk space
- **Network**: Stable internet connection

### Pre-installed Components
macOS includes these required components:
- **OpenSSH**: Built-in SSH client
- **Python 3**: Available via Xcode Command Line Tools
- **Curl/Wget**: Built-in download utilities

### Optional Components
- **Homebrew**: For additional package management
- **Xcode Command Line Tools**: For development features
- **Python 3 (Homebrew)**: For latest Python features

## Download & Installation

### Method 1: Quick Download (Recommended)

**Download the latest macOS build:**
- **File**: `polaris-node-manager-macos.zip`
- **Size**: 891 MB (Universal Binary)
- **URL**: [GitHub Releases v2.0.2](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.2)

### Method 2: Command Line Download

```bash
# Create download directory
mkdir -p ~/Downloads/polaris-v2.0.2
cd ~/Downloads/polaris-v2.0.2

# Download using curl
curl -L -o polaris-v2.0.2-macos.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-macos.zip

# Extract
unzip polaris-v2.0.2-macos.zip
cd polaris-node-manager-macos
```

## Installation Process

### Standard Installation (Recommended)

1. **Install via PKG Installer:**
   ```bash
   # Double-click the PKG file or run from terminal
   sudo installer -pkg polaris-node-manager.pkg -target /
   ```

2. **Security Permissions:**
   - macOS may show security warning for unsigned application
   - Go to **System Preferences** → **Security & Privacy** → **General**
   - Click "Allow" when prompted or "Open Anyway"

3. **Post-Installation:**
   - Application installed to `/Applications/Polaris Node Manager.app`
   - Available in Launchpad and Spotlight
   - Automatic PATH configuration for command line access

### Alternative Installation Methods

#### Drag & Drop Installation
```bash
# Mount the disk image (if DMG provided)
open polaris-node-manager.dmg

# Drag application to Applications folder
# Or copy via command line
cp -r "Polaris Node Manager.app" /Applications/
```

#### Homebrew Installation (Community Cask)
```bash
# Install via Homebrew Cask (if available)
brew install --cask polaris-node-manager

# Or add custom tap
brew tap bigideaafrica/polaris
brew install --cask polaris-node-manager
```

### Handling macOS Security Restrictions

#### Gatekeeper Bypass
If macOS blocks the application due to Gatekeeper:

```bash
# Remove quarantine attribute
sudo xattr -rd com.apple.quarantine "/Applications/Polaris Node Manager.app"

# Or allow specific app
sudo spctl --add "/Applications/Polaris Node Manager.app"
sudo spctl --enable --label "Polaris Node Manager"
```

#### Privacy Permissions
Grant necessary permissions:
1. **System Preferences** → **Security & Privacy** → **Privacy**
2. Enable permissions for:
   - **Full Disk Access** (for SSH key access)
   - **Network** (for API connections)
   - **Automation** (for background operations)

## Using v2.0.2 Features on macOS

### Setting Up SSH Connections

#### Method 1: Direct Key Input (New in v2.0.2)

1. **Launch Application:**
   ```bash
   # From Applications folder
   open "/Applications/Polaris Node Manager.app"
   
   # From command line
   /Applications/Polaris\ Node\ Manager.app/Contents/MacOS/polaris-node-manager
   
   # Via Spotlight
   # Press Cmd+Space, type "Polaris"
   ```

2. **Add New Machine:**
   - Click "Add Machine" button
   - Enter machine details:
     - **Hostname/IP**: Target machine address
     - **Username**: SSH username
     - **Port**: SSH port (default: 22)

3. **SSH Key Setup:**
   - **Option A - Direct Paste** (Recommended):
     - Copy your SSH private key content:
       ```bash
       cat ~/.ssh/id_rsa  # or your key file
       # Use Cmd+C to copy the output
       ```
     - Paste directly into "SSH Private Key" text area using Cmd+V
     - System validates key format automatically
   
   - **Option B - Load from File**:
     - Click "Load Key from File" button
     - Use native macOS file dialog to navigate to key file
     - Common location: `~/.ssh/` (may be hidden in Finder)

4. **Connect:**
   - Click "Connect" button
   - Monitor connection status in real-time
   - Enhanced error messages guide troubleshooting

#### SSH Key Management on macOS

**Accessing SSH Keys in Finder:**
```bash
# Show hidden files in Finder
defaults write com.apple.finder AppleShowAllFiles -bool true
killall Finder

# Or use keyboard shortcut: Cmd+Shift+. (period)
```

**Common SSH key locations:**
```bash
# List SSH keys
ls -la ~/.ssh/

# Common key files:
# ~/.ssh/id_rsa (RSA private key)
# ~/.ssh/id_ed25519 (Ed25519 private key)
# ~/.ssh/id_ecdsa (ECDSA private key)
# ~/.ssh/your-server.pem (AWS/cloud provider keys)
```

**Generating SSH Keys on macOS:**
```bash
# Generate Ed25519 key (recommended)
ssh-keygen -t ed25519 -C "your-email@example.com" -f ~/.ssh/polaris_key

# Generate RSA key (traditional)
ssh-keygen -t rsa -b 4096 -C "your-email@example.com" -f ~/.ssh/polaris_key

# Set proper permissions
chmod 600 ~/.ssh/polaris_key
chmod 644 ~/.ssh/polaris_key.pub
```

**Keychain Integration:**
```bash
# Add SSH key to macOS Keychain
ssh-add --apple-use-keychain ~/.ssh/polaris_key

# List keys in Keychain
ssh-add -l

# Configure SSH to use Keychain
cat >> ~/.ssh/config << EOF
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/polaris_key
EOF
```

### macOS-Specific Enhanced Features

#### Menu Bar Integration

Enable menu bar mode for quick access:
- **Polaris** → **Preferences** → **General**
- Check "Show in menu bar"
- Application icon appears in menu bar for quick status

#### Notification Center Integration

Configure system notifications:
- **System Preferences** → **Notifications & Focus** → **Polaris Node Manager**
- Enable alerts for connection status changes
- Configure notification style (banners, alerts, none)

#### Spotlight Integration

Application is automatically indexed by Spotlight:
```bash
# Search for Polaris in Spotlight (Cmd+Space)
# Type: "Polaris" or "Node Manager"

# Force Spotlight reindex if needed
sudo mdutil -E /Applications
```

#### Touch Bar Support (MacBook Pro)

For MacBook Pro with Touch Bar:
- Connection status indicators
- Quick machine selection buttons
- SSH key loading shortcuts

### macOS-Specific Troubleshooting

#### Application Won't Launch

**Problem**: App damaged or can't be opened
**Solution**: Remove quarantine and update permissions

```bash
# Remove quarantine
sudo xattr -rd com.apple.quarantine "/Applications/Polaris Node Manager.app"

# Fix permissions
sudo chmod -R 755 "/Applications/Polaris Node Manager.app"

# Repair app bundle
sudo codesign --force --deep --sign - "/Applications/Polaris Node Manager.app"
```

#### SSH Key Access Issues

**Problem**: Cannot access SSH keys in ~/.ssh/
**Solution**: Grant Full Disk Access permission

1. **System Preferences** → **Security & Privacy** → **Privacy**
2. Select **Full Disk Access**
3. Click lock icon and authenticate
4. Click "+" and add Polaris Node Manager

#### Network Connection Issues

**Problem**: API connections blocked by firewall
**Solution**: Configure macOS firewall

```bash
# Check firewall status
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate

# Add firewall exception
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add "/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager"
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblock "/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager"
```

#### Python Dependencies (if needed)

**Problem**: Python-related errors
**Solution**: Install Python dependencies

```bash
# Using built-in Python
pip3 install --user paramiko psutil

# Using Homebrew Python
brew install python
/opt/homebrew/bin/pip3 install paramiko psutil

# Set Python path for Polaris
defaults write com.bigideaafrica.polaris-node-manager PythonPath "/opt/homebrew/bin/python3"
```

#### Performance Issues on Apple Silicon

**Problem**: Application runs slowly on M1/M2/M3 Macs
**Solution**: Verify native Apple Silicon support

```bash
# Check if running natively
arch
# Should show "arm64" on Apple Silicon

# Check application architecture
file "/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager"
# Should show "universal binary" or "arm64"

# Force native execution
arch -arm64 "/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager"
```

### Performance Optimization for macOS

#### System Optimization

```bash
# Increase file descriptor limits
echo 'limit maxfiles 65536 65536' | sudo tee -a /etc/launchd.conf

# Optimize network settings
sudo sysctl -w net.inet.tcp.delayed_ack=0
```

#### Resource Monitoring

```bash
# Monitor Polaris processes
ps aux | grep -i polaris
top -pid $(pgrep -f polaris)

# Monitor network connections
netstat -an | grep -i polaris
lsof -nP -iTCP -sTCP:ESTABLISHED | grep polaris

# System resource monitoring
Activity\ Monitor.app  # GUI tool
htop  # Install via: brew install htop
```

## Advanced macOS Configuration

### Launch Agents (Auto-start)

Create a Launch Agent for automatic startup:

```bash
# Create launch agent directory
mkdir -p ~/Library/LaunchAgents

# Create launch agent plist
cat > ~/Library/LaunchAgents/com.bigideaafrica.polaris-node-manager.plist << EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>Label</key>
    <string>com.bigideaafrica.polaris-node-manager</string>
    <key>ProgramArguments</key>
    <array>
        <string>/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager</string>
        <string>--background</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>KeepAlive</key>
    <false/>
</dict>
</plist>
EOF

# Load launch agent
launchctl load ~/Library/LaunchAgents/com.bigideaafrica.polaris-node-manager.plist

# Enable auto-start
launchctl enable gui/$(id -u)/com.bigideaafrica.polaris-node-manager
```

### Preferences and Configuration

```bash
# Application preferences location
~/Library/Preferences/com.bigideaafrica.polaris-node-manager.plist

# Configuration files
~/Library/Application Support/Polaris Node Manager/
├── config.json
├── machines.json
├── logs/
└── ssh_keys/

# Cache files
~/Library/Caches/com.bigideaafrica.polaris-node-manager/
```

### Shell Integration

Add to your shell profile (`~/.zshrc` or `~/.bash_profile`):

```bash
# Aliases for easy access
alias polaris='"/Applications/Polaris Node Manager.app/Contents/MacOS/polaris-node-manager"'
alias polaris-logs='tail -f ~/Library/Application\ Support/Polaris\ Node\ Manager/logs/app.log'

# Function to quick-launch with specific machine
polaris-connect() {
    polaris --connect "$1"
}
```

## Uninstallation

### Complete Removal

```bash
# Remove application
sudo rm -rf "/Applications/Polaris Node Manager.app"

# Remove preferences
rm -f ~/Library/Preferences/com.bigideaafrica.polaris-node-manager.plist

# Remove application support files
rm -rf ~/Library/Application\ Support/Polaris\ Node\ Manager/

# Remove caches
rm -rf ~/Library/Caches/com.bigideaafrica.polaris-node-manager/

# Remove launch agent (if created)
launchctl unload ~/Library/LaunchAgents/com.bigideaafrica.polaris-node-manager.plist
rm -f ~/Library/LaunchAgents/com.bigideaafrica.polaris-node-manager.plist

# Remove Keychain entries (optional)
security delete-generic-password -s "Polaris Node Manager" -a "SSH Keys"
```

### Using Third-Party Uninstallers

```bash
# AppCleaner (recommended)
# Download from: https://freemacsoft.net/appcleaner/

# Or use Homebrew
brew install --cask appcleaner
```

## Migration from v2.0.1

v2.0.2 automatically migrates existing macOS configurations:

```bash
# Configuration migration
~/Library/Application Support/Polaris Node Manager v2.0.1/
↓
~/Library/Application Support/Polaris Node Manager/

# Manual backup (optional)
cp -r ~/Library/Application\ Support/Polaris\ Node\ Manager\ v2.0.1/ \
      ~/Library/Application\ Support/Polaris\ Node\ Manager\ Backup/
```

## Support Resources

### macOS-Specific Debugging

```bash
# Console logs
log show --predicate 'subsystem contains "polaris"' --last 1h

# Crash reports
ls ~/Library/Logs/DiagnosticReports/*polaris*

# System logs
tail -f /var/log/system.log | grep -i polaris
```

### Getting Help
- **GitHub Issues**: [macOS-specific issues](https://github.com/bigideaafrica/polaris_distributions/issues)
- **In-App Support**: Contact Support feature with machine selection
- **Apple Support**: For macOS-specific system issues

### Useful macOS Commands

```bash
# System information
system_profiler SPSoftwareDataType
system_profiler SPHardwareDataType

# Network configuration
networksetup -listallhardwareports
ifconfig | grep -E "inet |ether "

# Check running processes
launchctl list | grep polaris
```

---

**macOS Installation Complete!** You're now ready to use Polaris Node Manager v2.0.2 with enhanced connection system and optimized macOS integration on both Intel and Apple Silicon Macs. 