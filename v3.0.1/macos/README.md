# Polaris Node Manager v3.0.1 - macOS

macOS distribution of Polaris Node Manager v3.0.1 with native Apple Silicon optimization, seamless macOS integration, and enterprise-grade security features.

## 📦 Available Downloads

### macOS Universal Build
- **File**: `polaris-node-manager-macos-v3.0.1.dmg`
- **Architecture**: Universal Binary (Intel x86_64 + Apple Silicon ARM64)
- **Format**: DMG installer with application bundle
- **Size**: ~175MB (compressed)
- **Compatibility**: macOS 12.0 (Monterey) or later

### Alternative Downloads
- **ZIP Archive**: `polaris-node-manager-macos-v3.0.1.zip` (for automated deployment)
- **PKG Installer**: `polaris-node-manager-v3.0.1.pkg` (for enterprise deployment)

## 🔧 Installation Options

### Option 1: DMG Installer (Recommended)

1. **Download and Mount DMG**:
   ```bash
   # Download DMG file
   curl -L -o polaris-v3.0.1.dmg [download-url]
   
   # Mount DMG
   hdiutil mount polaris-v3.0.1.dmg
   ```

2. **Install Application**:
   - Open the mounted DMG
   - Drag "Polaris Node Manager.app" to Applications folder
   - Or use command line:
   ```bash
   cp -R "/Volumes/Polaris Node Manager/Polaris Node Manager.app" /Applications/
   ```

3. **Launch Application**:
   - Open from Applications folder
   - Or use Spotlight: ⌘+Space, type "Polaris"
   - Or from Terminal: `open -a "Polaris Node Manager"`

4. **First Launch Security**:
   - Right-click the app and select "Open"
   - Click "Open" in the security dialog
   - Or go to System Preferences > Security & Privacy > General

### Option 2: Command Line Installation

```bash
# Download and install via command line
curl -L -o polaris-v3.0.1.dmg [download-url]
hdiutil mount polaris-v3.0.1.dmg
cp -R "/Volumes/Polaris Node Manager/Polaris Node Manager.app" /Applications/
hdiutil unmount "/Volumes/Polaris Node Manager"

# Add to PATH (optional)
sudo ln -sf "/Applications/Polaris Node Manager.app/Contents/MacOS/polaris" /usr/local/bin/polaris

# Launch from terminal
polaris
```

### Option 3: Homebrew Installation (Coming Soon)

```bash
# Add Polaris tap
brew tap bigideaafrica/polaris

# Install Polaris Node Manager
brew install --cask polaris-node-manager

# Launch application
open -a "Polaris Node Manager"
```

### Option 4: Enterprise PKG Installation

```bash
# Install PKG package (requires administrator privileges)
sudo installer -pkg polaris-node-manager-v3.0.1.pkg -target /

# Verify installation
/Applications/Polaris\ Node\ Manager.app/Contents/MacOS/polaris --version
```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: macOS 12.0 (Monterey) or later
- **Architecture**: Intel x86_64 or Apple Silicon (M1/M2/M3)
- **RAM**: 16GB minimum (32GB recommended for enterprise workloads)
- **Storage**: 10GB free disk space (SSD recommended)
- **CPU**: 4 cores minimum (8+ cores recommended)
- **Network**: Broadband internet connection

### Recommended Requirements
- **OS**: macOS 14.0 (Sonoma) or later
- **Hardware**: MacBook Pro/Mac Studio/Mac Pro with Apple Silicon
- **RAM**: 32GB or more (64GB for AI workloads)
- **Storage**: 50GB+ available on fast SSD
- **Network**: Gigabit ethernet or Wi-Fi 6

### Apple Silicon Optimization
- **Native ARM64**: Fully optimized for M1/M2/M3 chips
- **Rosetta 2**: Intel compatibility when needed
- **Metal Performance**: GPU acceleration for AI workloads
- **Neural Engine**: AI model acceleration on supported hardware

## 🔧 Prerequisites and Dependencies

### Required macOS Tools

Most dependencies are bundled, but some system tools are required:

```bash
# Install Xcode Command Line Tools
xcode-select --install

# Install Homebrew (recommended package manager)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install essential tools
brew install curl wget git python3 node
```

### Docker Desktop for Mac

```bash
# Install Docker Desktop
brew install --cask docker

# Or download from Docker website
curl -L -o Docker.dmg https://desktop.docker.com/mac/main/arm64/Docker.dmg
hdiutil mount Docker.dmg
cp -R "/Volumes/Docker/Docker.app" /Applications/
hdiutil unmount /Volumes/Docker

# Launch Docker Desktop
open -a Docker

# Verify Docker installation
docker --version
docker compose version
```

### Kubernetes Tools

```bash
# Install kubectl
brew install kubectl

# Install Helm
brew install helm

# Install k9s (Kubernetes CLI)
brew install k9s

# Install kind (local Kubernetes)
brew install kind

# Verify installations
kubectl version --client
helm version
```

## 🚀 First-Time Setup

### 1. Launch Polaris Node Manager

```bash
# From Applications
open -a "Polaris Node Manager"

# From Terminal
polaris

# Check if running
ps aux | grep polaris
```

### 2. macOS Permissions Setup

Polaris may request the following permissions:

1. **Network Access**: For cloud provider communication
2. **Full Disk Access**: For container and VM management
3. **Accessibility**: For UI automation features
4. **Camera/Microphone**: For video conferencing integration (optional)

To grant permissions:
```bash
# Open System Preferences
open "x-apple.systempreferences:com.apple.preference.security"

# Or use command line to check permissions
tccutil reset All com.bigideaafrica.polaris-node-manager
```

### 3. Complete Setup Wizard

1. **Welcome Screen**: Choose setup type (Quick/Advanced)
2. **macOS Integration**:
   - Enable Keychain integration
   - Configure Touch ID/Face ID authentication
   - Set up Notification Center integration
3. **Cloud Provider Configuration**:
   ```bash
   # AWS CLI setup
   brew install awscli
   aws configure
   
   # Azure CLI setup
   brew install azure-cli
   az login
   
   # Google Cloud CLI setup
   brew install google-cloud-sdk
   gcloud auth login
   ```

4. **Container Runtime Configuration**:
   ```bash
   # Configure Docker for Polaris
   polaris docker configure
   
   # Test Docker connectivity
   docker run hello-world
   ```

### 4. macOS-Specific Configuration

```bash
# Configure LaunchAgent for auto-start
polaris service install --user

# Configure Keychain integration
polaris keychain setup

# Enable Touch ID authentication
polaris touchid enable

# Configure Notification Center
polaris notifications setup
```

## 🛡️ macOS Security Integration

### Keychain Integration
```bash
# Store cloud credentials in Keychain
polaris keychain add-aws-credentials
polaris keychain add-azure-credentials
polaris keychain add-gcp-credentials

# List stored credentials
polaris keychain list

# Update credentials
polaris keychain update aws --access-key-id NEW_KEY
```

### Touch ID / Face ID Authentication
```bash
# Enable biometric authentication
polaris auth enable-biometric

# Configure for sudo operations
polaris auth configure-sudo

# Test biometric authentication
polaris auth test-biometric
```

### Code Signing and Notarization
- **Developer ID**: Signed with Apple Developer ID certificate
- **Notarized**: Notarized by Apple for Gatekeeper compatibility
- **Hardened Runtime**: Enhanced security with hardened runtime
- **Entitlements**: Minimal required entitlements for security

### System Integrity Protection (SIP)
```bash
# Check SIP status
csrutil status

# Polaris works with SIP enabled
# No SIP modifications required
```

## 🔧 macOS-Specific Features

### Menu Bar Integration
- **Status Menu**: Real-time system status in menu bar
- **Quick Actions**: Common tasks accessible from menu bar
- **Notifications**: Native macOS notifications for alerts
- **Dark Mode**: Full Dark Mode support with system preference sync

### Shortcuts and Automation
```bash
# Create Shortcuts for common tasks
polaris shortcuts create

# Integrate with Automator
polaris automator setup

# Configure Siri shortcuts (macOS 12+)
polaris siri setup
```

### Native macOS Services
```bash
# Enable Services menu integration
polaris services enable

# Configure Spotlight integration
polaris spotlight configure

# Set up Quick Look plugins
polaris quicklook install
```

### Universal Control and Continuity
- **Handoff**: Start tasks on iPhone/iPad, continue on Mac
- **Universal Clipboard**: Copy deployment commands between devices
- **AirDrop**: Share configuration files between Apple devices

## 🐳 Container Management on macOS

### Docker Desktop Configuration

```bash
# Configure Docker Desktop for optimal performance
polaris docker optimize-macos

# Configure resource allocation
polaris docker set-resources --memory 16GB --cpu 8

# Enable Kubernetes in Docker Desktop
polaris docker enable-kubernetes

# Configure file sharing for better performance
polaris docker configure-file-sharing
```

### Lima (Alternative to Docker Desktop)

```bash
# Install Lima
brew install lima

# Create Lima VM for containers
polaris lima create --name polaris-vm

# Start Lima VM
polaris lima start polaris-vm

# Configure Polaris to use Lima
polaris container-runtime set lima
```

### Podman on macOS

```bash
# Install Podman
brew install podman

# Initialize Podman machine
podman machine init

# Start Podman machine
podman machine start

# Configure Polaris for Podman
polaris container-runtime set podman
```

## 📊 Performance Optimization for macOS

### Apple Silicon Optimization

```bash
# Enable Apple Silicon optimizations
polaris optimize apple-silicon

# Configure Metal GPU acceleration
polaris gpu configure-metal

# Enable Neural Engine for AI workloads
polaris ai enable-neural-engine

# Monitor performance
polaris performance monitor --apple-silicon
```

### Memory Management

```bash
# Configure memory pressure handling
polaris memory configure-pressure-handling

# Enable memory compression
polaris memory enable-compression

# Configure swap usage
polaris memory configure-swap
```

### Storage Optimization

```bash
# Enable APFS optimizations
polaris storage optimize-apfs

# Configure Time Machine exclusions
polaris storage configure-time-machine-exclusions

# Set up storage monitoring
polaris storage monitor --threshold 80%
```

## 🔄 Updates and Maintenance

### Automatic Updates

```bash
# Enable automatic updates
polaris updates enable-auto

# Configure update schedule
polaris updates schedule --check-interval 24h

# Configure update notifications
polaris updates notifications enable
```

### Manual Updates

```bash
# Check for updates
polaris updates check

# Download updates
polaris updates download

# Install updates
polaris updates install

# Restart if required
polaris updates restart-if-needed
```

### Maintenance Tasks

```bash
# Clean up temporary files
polaris maintenance cleanup

# Optimize database
polaris maintenance optimize-db

# Check system health
polaris maintenance health-check

# Generate maintenance report
polaris maintenance report --output ~/Desktop/polaris-maintenance.pdf
```

## 🐛 Troubleshooting

### Common macOS Issues

**Application won't launch**:
```bash
# Check Gatekeeper status
spctl --status

# Reset application permissions
xattr -cr "/Applications/Polaris Node Manager.app"

# Re-sign application (if needed)
codesign --force --deep --sign - "/Applications/Polaris Node Manager.app"
```

**Docker Desktop issues**:
```bash
# Reset Docker Desktop
docker system prune -a

# Restart Docker Desktop
osascript -e 'quit app "Docker Desktop"'
sleep 5
open -a "Docker Desktop"

# Check Docker Desktop status
docker system info
```

**Permission issues**:
```bash
# Reset TCC database for Polaris
tccutil reset All com.bigideaafrica.polaris-node-manager

# Grant Full Disk Access manually
open "x-apple.systempreferences:com.apple.preference.security?Privacy_AllFiles"
```

**Network connectivity issues**:
```bash
# Check network configuration
networksetup -listallnetworkservices

# Flush DNS cache
sudo dscacheutil -flushcache

# Test connectivity
polaris network diagnose

# Reset network settings (if needed)
polaris network reset-settings
```

### Performance Issues

**High CPU usage**:
```bash
# Monitor CPU usage
top -pid $(pgrep polaris)

# Check for background processes
polaris process list

# Optimize CPU usage
polaris optimize cpu
```

**Memory issues**:
```bash
# Check memory usage
memory_pressure

# Free memory
sudo purge

# Configure memory limits
polaris memory set-limits --max 16GB
```

**Slow container operations**:
```bash
# Check Docker Desktop resources
docker system df

# Optimize Docker storage
docker system prune -a

# Configure Docker for better performance
polaris docker optimize-performance
```

### Log Analysis

```bash
# View application logs
polaris logs view --level info

# View system logs
log show --predicate 'process == "polaris"' --last 1h

# Export logs for support
polaris logs export --format json --output ~/Desktop/polaris-logs.json

# Check crash reports
polaris logs crashes
```

## 📚 macOS-Specific Resources

### Documentation
- **macOS Installation Guide**: [docs.polaris.bigideaafrica.com/macos](https://docs.polaris.bigideaafrica.com/macos)
- **Apple Silicon Optimization**: [docs.polaris.bigideaafrica.com/apple-silicon](https://docs.polaris.bigideaafrica.com/apple-silicon)
- **macOS Security Guide**: [docs.polaris.bigideaafrica.com/security/macos](https://docs.polaris.bigideaafrica.com/security/macos)
- **Keychain Integration**: [docs.polaris.bigideaafrica.com/keychain](https://docs.polaris.bigideaafrica.com/keychain)

### Community Resources
- **macOS Users Forum**: [community.polaris.bigideaafrica.com/c/macos](https://community.polaris.bigideaafrica.com/c/macos)
- **Apple Silicon Discussion**: [community.polaris.bigideaafrica.com/c/apple-silicon](https://community.polaris.bigideaafrica.com/c/apple-silicon)
- **macOS Automation**: [community.polaris.bigideaafrica.com/c/macos-automation](https://community.polaris.bigideaafrica.com/c/macos-automation)

### Scripts and Automations
- **macOS Scripts**: [github.com/bigideaafrica/polaris-macos-scripts](https://github.com/bigideaafrica/polaris-macos-scripts)
- **Shortcuts Gallery**: [github.com/bigideaafrica/polaris-shortcuts](https://github.com/bigideaafrica/polaris-shortcuts)
- **Automator Workflows**: [github.com/bigideaafrica/polaris-automator](https://github.com/bigideaafrica/polaris-automator)

## 📞 macOS Support

### macOS-Specific Support Channels
- **macOS Technical Support**: macos-support@polaris.bigideaafrica.com
- **Apple Silicon Support**: apple-silicon-support@polaris.bigideaafrica.com
- **Enterprise macOS Support**: enterprise-macos@polaris.bigideaafrica.com
- **Developer Support**: developer-support@polaris.bigideaafrica.com

### Apple Partnership
Polaris Node Manager is part of the Apple Developer Program with:
- **Mac App Store**: Available for enterprise customers
- **Apple Business Manager**: Integration for enterprise deployment
- **Apple Configurator**: Support for mass deployment
- **TestFlight**: Beta testing program for early features

## 🎯 Advanced macOS Integration

### Shortcuts and Siri

```bash
# Create Siri shortcuts for common tasks
polaris siri create-shortcuts

# Voice commands examples:
# "Hey Siri, deploy my web app"
# "Hey Siri, check cluster status"
# "Hey Siri, scale my deployment"
```

### Focus Modes Integration

```bash
# Configure Focus modes integration
polaris focus configure

# Automatically adjust notifications based on Focus mode
# Work Focus: Show only critical alerts
# Do Not Disturb: Suppress all notifications
# Personal: Show all notifications
```

### Stage Manager Support

- **Window Management**: Automatic window grouping for related tasks
- **Scene Organization**: Organize deployment workflows in scenes
- **Multi-Display**: Optimal layout across multiple displays

---

**Build Information**:
- **Build Date**: Latest development build
- **Architecture**: Universal Binary (x86_64 + ARM64)
- **Minimum macOS**: 12.0 (Monterey)
- **Code Signing**: Developer ID Application certificate
- **Notarization**: Apple notarized for Gatekeeper
- **Hardened Runtime**: Enabled with minimal entitlements
- **Dependencies**: Bundled with native macOS frameworks

**Note**: For the best experience on macOS, we recommend using the latest macOS version with Apple Silicon hardware. The application is fully optimized for Apple Silicon and includes specific optimizations for M1/M2/M3 chips, Metal GPU acceleration, and Neural Engine support for AI workloads.
