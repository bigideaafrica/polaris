# Polaris Node Manager v3.0.0 - macOS

Native macOS distribution of Polaris Node Manager v3.0.0 with universal binary support for both Intel and Apple Silicon processors.

## 📦 Available Downloads

### macOS Latest Build
- **File**: `macos-latest-build.zip`
- **Architecture**: Universal Binary (Intel x86_64 + Apple Silicon ARM64)
- **Format**: ZIP containing .app bundle and installation resources
- **Size**: ~200MB (compressed)
- **Compatibility**: macOS 12.0 (Monterey) or later

## 🔧 Installation

### Quick Installation (Recommended)

1. **Download and Extract**:
   ```bash
   curl -L -o polaris-v3-macos.zip [download-url]
   unzip polaris-v3-macos.zip
   ```

2. **Install Application**:
   ```bash
   # Move to Applications folder
   sudo cp -R "Polaris Node Manager.app" /Applications/
   
   # Or drag and drop to Applications folder in Finder
   ```

3. **First Launch**:
   - Open **Launchpad** or **Applications** folder
   - Click **Polaris Node Manager**
   - Allow security permissions when prompted

### Manual Installation

1. **Extract the ZIP file**:
   ```bash
   unzip macos-latest-build.zip
   ```

2. **Verify Code Signature** (recommended):
   ```bash
   codesign -dv --verbose=4 "Polaris Node Manager.app"
   spctl -a -t exec -vv "Polaris Node Manager.app"
   ```

3. **Install Dependencies** (if needed):
   ```bash
   # Install Homebrew (if not already installed)
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   
   # Install required tools
   brew install docker docker-compose
   ```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: macOS 12.0 (Monterey) or later
- **Processor**: Intel Core i5 (2015+) or Apple M1/M2
- **RAM**: 8GB minimum (16GB recommended)
- **Storage**: 5GB free disk space
- **Network**: Broadband internet connection

### Recommended Requirements
- **OS**: macOS 13.0 (Ventura) or later
- **Processor**: Apple M1 Pro/Max/Ultra or Intel Core i7/i9
- **RAM**: 16GB or more
- **Storage**: 20GB+ SSD storage
- **Network**: High-speed internet (50+ Mbps for cloud operations)

### Processor Compatibility
- **Apple Silicon**: M1, M1 Pro, M1 Max, M1 Ultra, M2, M2 Pro, M2 Max, M2 Ultra
- **Intel**: Core i5/i7/i9 (2015 or later), Xeon processors

## 🍎 macOS-Specific Features

### Native Integration
- **Menu Bar Integration**: Quick access to status and controls
- **Notification Center**: Native macOS notifications for events
- **Spotlight Search**: Search for Polaris resources from Spotlight
- **Touch Bar Support**: Quick actions on MacBook Pro Touch Bar
- **Retina Display**: Optimized for high-DPI displays

### Apple Silicon Optimization
- **Native ARM64**: Runs natively on Apple Silicon for optimal performance
- **Unified Memory**: Efficient memory usage with Apple's unified memory architecture
- **Power Efficiency**: Optimized for Apple Silicon's power management
- **Neural Engine**: Leverages Apple's Neural Engine for AI workloads

## 🔧 Dependencies & Prerequisites

### Required Dependencies
The installer will prompt to install these if missing:

```bash
# Xcode Command Line Tools
xcode-select --install

# Homebrew (recommended package manager)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Docker Desktop for Mac
brew install --cask docker
```

### Optional Dependencies
```bash
# Development tools
brew install git python3 node npm

# Container management
brew install kubectl helm

# Cloud CLI tools
brew install awscli azure-cli
brew install --cask google-cloud-sdk
```

## 🚀 Quick Start

1. **Launch Polaris Node Manager**:
   - From Applications folder
   - Or via Spotlight: `⌘ + Space`, type "Polaris"
   - Or via Terminal: `open -a "Polaris Node Manager"`

2. **Grant Permissions**:
   - **Security & Privacy**: Allow app to run
   - **Network**: Allow incoming/outgoing connections
   - **Full Disk Access**: For container management (if prompted)

3. **Complete Setup**:
   - Follow the macOS-optimized setup wizard
   - Configure cloud provider credentials
   - Set up Docker Desktop integration

## 🔒 Security & Privacy

### Gatekeeper & Notarization
- App is **notarized** by Apple for security
- **Code signed** with valid Developer ID
- Passes all **Gatekeeper** security checks

### Required Permissions
The app may request these permissions:
- **Network Access**: For cloud API communication
- **Keychain Access**: For secure credential storage
- **Full Disk Access**: For Docker container management
- **Accessibility**: For advanced automation features

### Security Best Practices
```bash
# Verify app signature
codesign --verify --deep --strict "Polaris Node Manager.app"

# Check for malware (optional)
sudo xattr -d com.apple.quarantine "Polaris Node Manager.app"

# Enable FileVault for disk encryption
sudo fdesetup enable
```

## 🐳 Docker Integration

### Docker Desktop Setup
1. **Install Docker Desktop**:
   ```bash
   brew install --cask docker
   ```

2. **Configure Docker**:
   - Launch Docker Desktop
   - Sign in to Docker Hub (optional)
   - Allocate resources: **8GB RAM**, **4 CPUs** minimum

3. **Verify Installation**:
   ```bash
   docker --version
   docker-compose --version
   ```

### Container Management
- **Native Docker Integration**: Seamless container orchestration
- **Resource Monitoring**: Real-time container resource usage
- **Volume Management**: Persistent storage for containers
- **Network Configuration**: Custom Docker networks

## 🔄 Updates & Maintenance

### Automatic Updates
- **Built-in Updater**: Checks for updates on startup
- **Background Downloads**: Updates download in background
- **One-Click Install**: Simple update installation process
- **Rollback Support**: Option to revert to previous version

### Manual Updates
```bash
# Check current version
open -a "Polaris Node Manager" --args --version

# Download latest version
curl -L -o polaris-v3-latest.zip [latest-download-url]

# Backup current settings
cp -R ~/Library/Application\ Support/Polaris\ Node\ Manager ~/Desktop/polaris-backup

# Install new version
unzip polaris-v3-latest.zip
sudo cp -R "Polaris Node Manager.app" /Applications/
```

## 🐛 Troubleshooting

### Common Issues

**App won't open - "App is damaged"**:
```bash
# Remove quarantine attribute
sudo xattr -rd com.apple.quarantine "/Applications/Polaris Node Manager.app"

# Re-verify signature
codesign --verify --deep --strict "/Applications/Polaris Node Manager.app"
```

**Docker connection failed**:
```bash
# Start Docker Desktop
open -a Docker

# Verify Docker is running
docker info

# Reset Docker if needed
docker system prune -a
```

**Network connectivity issues**:
```bash
# Check DNS resolution
nslookup api.polaris.bigideaafrica.com

# Test HTTPS connectivity
curl -I https://api.polaris.bigideaafrica.com/health

# Check firewall settings
sudo /usr/libexec/ApplicationFirewall/socketfilterfw --getglobalstate
```

**Performance issues on Intel Macs**:
- Enable **Rosetta 2** if running Apple Silicon optimized containers
- Allocate more resources to Docker Desktop
- Close unnecessary applications to free up memory

### Log Files
Application logs are stored in:
- **Application Logs**: `~/Library/Logs/Polaris Node Manager/`
- **System Logs**: `/var/log/polaris/` (requires admin access)
- **Crash Reports**: `~/Library/Application Support/CrashReporter/`

## 🎯 Performance Optimization

### Apple Silicon Optimization
```bash
# Check if running native ARM64
arch
# Should return: arm64

# Verify native Docker images
docker info | grep Architecture
```

### Intel Mac Optimization
- **Memory Management**: Increase Docker Desktop memory allocation
- **CPU Allocation**: Assign 4+ CPU cores to Docker
- **Disk Space**: Ensure adequate free space for containers

## 📚 Additional Resources

- **Documentation**: [docs.polaris.bigideaafrica.com/macos](https://docs.polaris.bigideaafrica.com/macos)
- **macOS-specific guides**: [guides.polaris.bigideaafrica.com/macos](https://guides.polaris.bigideaafrica.com/macos)
- **Video tutorials**: [YouTube Channel](https://youtube.com/polarismanager)
- **Community forum**: [community.polaris.bigideaafrica.com](https://community.polaris.bigideaafrica.com)

## 📞 Support

For macOS-specific issues:
- **GitHub Issues**: [Report a bug](https://github.com/bigideaafrica/polaris_distributions/issues)
- **Community Support**: [macOS Discussion Forum](https://community.polaris.bigideaafrica.com/c/macos)
- **Email Support**: support@polaris.bigideaafrica.com
- **Documentation**: [macOS Installation Guide](https://docs.polaris.bigideaafrica.com/installation/macos)

## 🏷️ Version Information

- **Version**: 3.0.0 (Development Build)
- **Build Date**: Latest development snapshot
- **Architecture**: Universal Binary (x86_64 + ARM64)
- **Minimum macOS**: 12.0 (Monterey)
- **Code Signature**: Valid Apple Developer ID
- **Notarization**: Apple notarized for security

---

**Apple, macOS, and related terms are trademarks of Apple Inc.**
