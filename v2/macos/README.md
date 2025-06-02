# Polaris Node Manager v2.0.0 - macOS

Welcome to the macOS distribution of **Polaris Node Manager v2**! This package provides native macOS applications optimized for both Apple Silicon (M1/M2) and Intel-based Macs.

## 📦 Available Downloads

### DMG Installer (Recommended)
- **PolarisNodeManager-2.0.0.dmg** - Standard macOS installer with drag-and-drop installation
- **File Size**: ~130MB
- **Installation**: Drag to Applications folder
- **Updates**: Built-in update system
- **Compatibility**: Universal binary (Apple Silicon + Intel)

### Portable App
- **PolarisNodeManager-Portable.zip** - Standalone application bundle
- **File Size**: ~110MB compressed
- **Installation**: Extract and run from any location
- **Updates**: Manual download required
- **Compatibility**: Universal binary (Apple Silicon + Intel)

## 🔧 System Requirements

### Minimum Requirements
- **OS**: macOS 10.15 (Catalina) or later
- **Architecture**: Apple Silicon (M1/M2) or Intel (x64)
- **RAM**: 4GB minimum (8GB recommended)
- **Storage**: 500MB free disk space
- **Network**: Internet connection required
- **Permissions**: Administrator access for initial setup

### Recommended Configuration
- **OS**: macOS 12 (Monterey) or later
- **RAM**: 8GB+ for managing multiple machines
- **Storage**: 2GB+ free space (for logs and cache)
- **Network**: High-speed connection (50+ Mbps)
- **Display**: Retina display for optimal experience

### Apple Silicon vs Intel
- **Apple Silicon (M1/M2)**: Native ARM64 binary for optimal performance
- **Intel**: Native x64 binary with full feature compatibility
- **Rosetta 2**: Not required - native binaries for both architectures

## 🚀 Installation Instructions

### Method 1: DMG Installer (Recommended)

#### Option A: Download and Install
```bash
# Download DMG file
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v2/macos/PolarisNodeManager-2.0.0.dmg" -o "PolarisNodeManager-2.0.0.dmg"

# Open DMG (will mount automatically)
open PolarisNodeManager-2.0.0.dmg
```

#### Option B: Manual Installation
1. **Download** `PolarisNodeManager-2.0.0.dmg` from the repository
2. **Double-click** the DMG file to mount it
3. **Drag** "Polaris Node Manager" to the "Applications" folder
4. **Eject** the DMG file from Finder
5. **Launch** from Applications folder or Launchpad

#### Option C: Command Line Installation
```bash
# Mount DMG and copy to Applications
hdiutil attach PolarisNodeManager-2.0.0.dmg
cp -R "/Volumes/Polaris Node Manager/Polaris Node Manager.app" /Applications/
hdiutil detach "/Volumes/Polaris Node Manager"
```

### Method 2: Portable App

#### Extract and Run
```bash
# Download portable ZIP
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v2/macos/PolarisNodeManager-Portable.zip" -o "PolarisNodeManager-Portable.zip"

# Extract to current directory
unzip PolarisNodeManager-Portable.zip

# Run the application
open "Polaris Node Manager.app"
```

#### Alternative Extraction Locations
```bash
# Extract to Documents folder
unzip PolarisNodeManager-Portable.zip -d ~/Documents/

# Extract to Desktop
unzip PolarisNodeManager-Portable.zip -d ~/Desktop/

# Extract to custom location
unzip PolarisNodeManager-Portable.zip -d /path/to/custom/location/
```

## 🍎 macOS-Specific Setup

### First Launch Security
macOS may show a security warning for unsigned applications:

1. **Control+Click** on "Polaris Node Manager.app"
2. **Select** "Open" from the context menu
3. **Click** "Open" in the security dialog
4. **Alternative**: Go to System Preferences > Security & Privacy > General > "Open Anyway"

### Gatekeeper Bypass (Advanced Users)
```bash
# Remove quarantine attribute (run at your own risk)
sudo xattr -rd com.apple.quarantine "/Applications/Polaris Node Manager.app"

# Alternative: Disable Gatekeeper temporarily
sudo spctl --master-disable
# Re-enable after installation
sudo spctl --master-enable
```

### Keychain Access
The application may request keychain access for secure credential storage:
1. **Click** "Always Allow" when prompted
2. **Enter** your macOS password to grant access
3. **Check** "Save in Keychain" for convenience

## 📂 File Structure

### Installed Application
```
/Applications/Polaris Node Manager.app/
├── Contents/
│   ├── MacOS/
│   │   └── Polaris Node Manager         # Main executable
│   ├── Resources/                       # Application resources
│   ├── Info.plist                       # Application metadata
│   └── PkgInfo                         # Package information
```

### User Data Locations
```
~/Library/Application Support/PolarisNodeManager/
├── config.json                         # User configuration
├── logs/                               # Application logs
├── cache/                              # Cached data
└── wallet/                             # Wallet data (encrypted)
```

## 🏃‍♂️ Running the Application

### Launch Methods

#### From Applications Folder
1. **Open** Finder
2. **Navigate** to Applications folder
3. **Double-click** "Polaris Node Manager"

#### From Launchpad
1. **Click** Launchpad in Dock
2. **Search** for "Polaris Node Manager"
3. **Click** the application icon

#### From Terminal
```bash
# Launch application
open "/Applications/Polaris Node Manager.app"

# Launch with arguments
open "/Applications/Polaris Node Manager.app" --args --debug

# Background launch
nohup open "/Applications/Polaris Node Manager.app" &
```

### First Launch Setup
1. **Accept** macOS security prompts
2. **Allow** network access when prompted
3. **Complete** the initial setup wizard:
   - Create or import user account
   - Configure network settings
   - Set up Bittensor wallet (stored in Keychain)
   - Grant necessary permissions

### Adding Mining Machines
1. **Click** "Add Machine" button
2. **Enter** connection details:
   - Machine IP address
   - SSH credentials (stored securely in Keychain)
   - Custom port (if different from 22)
3. **Follow** the automated validation process
4. **Review** machine specifications and performance scores

## 🛠️ Configuration

### Application Settings
```bash
# Configuration file location
~/Library/Application Support/PolarisNodeManager/config.json

# Logs location
~/Library/Application Support/PolarisNodeManager/logs/

# Cache location
~/Library/Application Support/PolarisNodeManager/cache/
```

### Environment Variables
```bash
# Set custom configuration directory
export POLARIS_CONFIG_DIR="$HOME/.polaris-config"

# Enable debug logging
export POLARIS_DEBUG=true

# Set custom log level
export POLARIS_LOG_LEVEL=debug

# Disable automatic updates
export POLARIS_AUTO_UPDATE=false
```

### macOS System Integration

#### Dock Integration
```bash
# Keep in Dock permanently
# Right-click app in Dock > Options > Keep in Dock

# Remove from Dock
# Right-click app in Dock > Options > Remove from Dock
```

#### Login Items
```bash
# Add to login items (auto-start)
osascript -e 'tell application "System Events" to make login item at end with properties {path:"/Applications/Polaris Node Manager.app", hidden:false}'

# Remove from login items
osascript -e 'tell application "System Events" to delete login item "Polaris Node Manager"'
```

#### Notifications
Enable notifications in System Preferences:
1. **Open** System Preferences > Notifications & Focus
2. **Find** "Polaris Node Manager" in the list
3. **Enable** desired notification settings

## 🔐 Security & Privacy

### Network Permissions
The application requires network access for:
- **HTTPS**: API communications with Bittensor network
- **SSH**: Connections to mining machines
- **Updates**: Checking for application updates

### Keychain Integration
Sensitive data is stored securely in macOS Keychain:
- **SSH credentials**: Encrypted storage of machine credentials
- **Wallet keys**: Secure storage of cryptocurrency wallet information
- **API tokens**: Secure storage of authentication tokens

### Firewall Configuration
```bash
# Check firewall status
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate

# Add application to firewall exceptions
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --add "/Applications/Polaris Node Manager.app"
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --unblockapp "/Applications/Polaris Node Manager.app"
```

## 🧹 Maintenance

### Updating the Application
- **Automatic**: Built-in update system checks for new versions
- **Manual**: Check "Polaris Node Manager > Check for Updates" in menu bar
- **Portable**: Download new version and replace existing app

### Clearing Application Data
```bash
# Clear logs
rm -rf ~/Library/Application\ Support/PolarisNodeManager/logs/*

# Clear cache
rm -rf ~/Library/Application\ Support/PolarisNodeManager/cache/*

# Reset configuration (caution!)
rm -rf ~/Library/Application\ Support/PolarisNodeManager/config.json
```

### Backup Configuration
```bash
# Backup user configuration
tar -czf polaris-backup-$(date +%Y%m%d).tar.gz ~/Library/Application\ Support/PolarisNodeManager/

# Backup to iCloud (if enabled)
cp -R ~/Library/Application\ Support/PolarisNodeManager/ ~/Library/Mobile\ Documents/com~apple~CloudDocs/PolarisBackup/
```

### System Cleanup
```bash
# Clear system caches
sudo dscacheutil -flushcache

# Clear DNS cache
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder

# Reset network settings (if needed)
sudo dscacheutil -flushcache && sudo killall -HUP mDNSResponder
```

## 🚨 Troubleshooting

### Common Issues

#### Application Won't Launch
```bash
# Check system requirements
sw_vers

# Verify application integrity
codesign -v "/Applications/Polaris Node Manager.app"

# Check console logs
log show --predicate 'process == "Polaris Node Manager"' --last 1h
```

#### Permission Issues
```bash
# Fix application permissions
sudo chmod -R 755 "/Applications/Polaris Node Manager.app"

# Fix user data permissions
chmod -R 755 ~/Library/Application\ Support/PolarisNodeManager/
```

#### Network Connection Issues
```bash
# Test connectivity
curl -I https://api.bittensor.com

# Check DNS resolution
nslookup polariscloud.ai

# Test SSH connectivity
ssh -T user@your-mining-machine

# Check firewall status
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
```

#### Performance Issues on Apple Silicon
```bash
# Verify native Apple Silicon binary
file "/Applications/Polaris Node Manager.app/Contents/MacOS/Polaris Node Manager"
# Should show: Mach-O 64-bit executable arm64

# Force native mode (not needed for universal binary)
# Not applicable - app includes native ARM64 binary
```

#### Rosetta 2 Issues (Not Applicable)
This application provides native binaries for both Apple Silicon and Intel, so Rosetta 2 is not required.

### Debug Mode
```bash
# Launch with debug logging
open "/Applications/Polaris Node Manager.app" --args --debug

# View application logs
tail -f ~/Library/Application\ Support/PolarisNodeManager/logs/app.log

# View system logs
log stream --predicate 'process == "Polaris Node Manager"'
```

## 🔄 Uninstallation

### Complete Removal
```bash
# Remove application
sudo rm -rf "/Applications/Polaris Node Manager.app"

# Remove user data
rm -rf ~/Library/Application\ Support/PolarisNodeManager/

# Remove preferences
rm -rf ~/Library/Preferences/com.polaris.nodemanager.*

# Remove cache
rm -rf ~/Library/Caches/com.polaris.nodemanager/

# Remove from login items
osascript -e 'tell application "System Events" to delete login item "Polaris Node Manager"'

# Remove from Dock (if pinned)
# Manual: Right-click in Dock > Options > Remove from Dock
```

### Keychain Cleanup
```bash
# Remove stored credentials (optional)
security delete-generic-password -s "Polaris Node Manager" -a "user"

# Or use Keychain Access app:
# 1. Open Keychain Access
# 2. Search for "Polaris"
# 3. Delete related entries
```

## 📞 Support

### macOS-Specific Support
- **Console App**: Check macOS Console for application logs
- **Activity Monitor**: Monitor resource usage and performance
- **System Information**: Check hardware compatibility

### Apple Silicon vs Intel Issues
- **Architecture**: Use `arch` command to check running architecture
- **Performance**: Apple Silicon typically shows 2x better performance
- **Compatibility**: All features available on both architectures

### Getting Help
- 📧 **Email**: support@polarisnode.com
- 💬 **Discord**: [Join our community](https://discord.gg/polaris)
- 📖 **Documentation**: [Full docs](https://docs.polarisnode.com)
- 🐛 **Issues**: [GitHub Issues](https://github.com/BANADDA/polaris_distributions/issues)
- 🍎 **Apple Support**: [Apple Support](https://support.apple.com) for macOS-specific issues

## 📋 Command Line Usage

### Available Options
```bash
# Launch application
open "/Applications/Polaris Node Manager.app"

# Launch with custom configuration
open "/Applications/Polaris Node Manager.app" --args --config=/path/to/config.json

# Launch with debug logging
open "/Applications/Polaris Node Manager.app" --args --debug

# Launch in headless mode
"/Applications/Polaris Node Manager.app/Contents/MacOS/Polaris Node Manager" --headless

# Show version information
"/Applications/Polaris Node Manager.app/Contents/MacOS/Polaris Node Manager" --version
```

### Integration with Automator
Create an Automator workflow for custom shortcuts:
1. **Open** Automator
2. **Create** new "Application" workflow
3. **Add** "Run Shell Script" action
4. **Enter** launch command:
   ```bash
   open "/Applications/Polaris Node Manager.app"
   ```
5. **Save** as custom app

---

**Ready to manage your mining operations on macOS?** Download the DMG installer above and start monitoring your mining machines with native Apple performance! 🍎🚀
