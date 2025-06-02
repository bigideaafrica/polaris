# Polaris Node Manager v2.0.0 - Linux

Welcome to the Linux distribution of **Polaris Node Manager v2**! This package provides multiple installation options optimized for different Linux distributions and use cases.

## 📦 Available Downloads

### Linux Build (Recommended)
- **polaris-node-manager-linux.zip** - Universal Linux application bundle
- **File Size**: ~402 MB
- **Installation**: Extract ZIP and run
- **Updates**: Manual download required
- **Compatibility**: Works on most modern Linux distributions

### AppImage Alternative
- **Polaris Node Manager-0.17.1.AppImage** - Traditional AppImage format
- **File Size**: ~99MB
- **Installation**: Download and run - no system installation required
- **Updates**: Manual download required
- **Compatibility**: Universal Linux format

## 🔧 System Requirements

### Minimum Requirements
- **OS**: Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, Debian 11+)
- **Kernel**: Linux 4.18+
- **Architecture**: 64-bit (x86_64)
- **RAM**: 4GB minimum (8GB recommended)
- **Storage**: 500MB free disk space
- **Display**: X11 or Wayland with GTK3+ support
- **Network**: Internet connection required

### Recommended Configuration
- **OS**: Latest LTS distributions
- **RAM**: 8GB+ for managing multiple machines
- **Storage**: 2GB+ free space (for logs and cache)
- **Network**: High-speed connection (50+ Mbps)
- **Desktop**: GNOME, KDE, XFCE, or compatible

### Required Dependencies
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install -y libgtk-3-0 libnotify4 libnss3 libxss1 libxtst6 xdg-utils

# Fedora/RHEL/CentOS
sudo dnf install -y gtk3 libnotify nss libXss libXtst xdg-utils

# Arch Linux
sudo pacman -S gtk3 libnotify nss libxss libxtst xdg-utils
```

## 🚀 Installation Instructions

### Method 1: ZIP Build (Recommended)

#### Download and Extract
```bash
# Download Linux build
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager-linux.zip"

# Extract the file
unzip polaris-node-manager-linux.zip

# Make executable and run
chmod +x ./polaris-node-manager.AppImage
./polaris-node-manager.AppImage
```

#### Alternative Manual Extraction
1. **Download** `polaris-node-manager-linux.zip` from the repository
2. **Extract** using your file manager or command line
3. **Navigate** to the extracted folder
4. **Make executable**: `chmod +x polaris-node-manager.AppImage`
5. **Run** the application: `./polaris-node-manager.AppImage`

### Method 2: Direct AppImage

#### Download and Run
```bash
# Download AppImage directly
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/Polaris%20Node%20Manager-0.17.1.AppImage"

# Make executable
chmod +x "Polaris Node Manager-0.17.1.AppImage"

# Run the application
./"Polaris Node Manager-0.17.1.AppImage"
```

## 📂 File Structure

### ZIP Build Structure
```
polaris-node-manager-linux/
├── polaris-node-manager.AppImage       # Main application (AppImage format)
├── resources/                          # Application resources
├── lib/                               # Required libraries
├── data/                              # User data and configurations
├── logs/                              # Application logs
└── README.txt                         # Quick reference
```

### Direct AppImage Structure
```
Polaris Node Manager-0.17.1.AppImage    # Self-contained application
```

### Portable Structure
```
polaris-node-manager/
├── polaris-node-manager                   # Main executable
├── resources/                             # Application resources
├── lib/                                   # Shared libraries
├── data/                                  # User data and configurations
├── logs/                                  # Application logs
└── README.txt                            # Quick reference
```

## 🏃‍♂️ Running the Application

### From Package Installation
```bash
# Launch from command line
polaris-node-manager

# Launch from desktop
# Look for "Polaris Node Manager" in applications menu
```

### From AppImage
```bash
# Direct execution (x64)
./"Polaris Node Manager-0.17.1.AppImage"

# Direct execution (ARM64)
./"Polaris Node Manager-0.17.1-arm64.AppImage"

# Background execution
nohup ./"Polaris Node Manager-0.17.1.AppImage" &
```

### From Unpacked
```bash
# Navigate to unpacked directory and run (x64)
cd linux-unpacked
./"Polaris Node Manager"

# Navigate to unpacked directory and run (ARM64)
cd linux-arm64-unpacked
./"Polaris Node Manager"
```

### First Launch Setup
1. **Launch** Polaris Node Manager v2
2. **Grant** any required permissions
3. **Complete** the initial setup wizard:
   - Create or import user account
   - Configure network settings
   - Set up Bittensor wallet (if needed)

## 🛠️ Configuration

### Configuration Locations
```bash
# Package installation
~/.config/polaris-node-manager/config.json

# AppImage
~/.config/polaris-node-manager/config.json

# Portable
./data/config.json
```

### Log Locations
```bash
# Package installation
~/.local/share/polaris-node-manager/logs/

# AppImage
~/.local/share/polaris-node-manager/logs/

# Portable
./logs/
```

### Environment Variables
```bash
# Set custom configuration directory
export POLARIS_CONFIG_DIR="/path/to/config"

# Enable debug logging
export POLARIS_DEBUG=true

# Set custom log level
export POLARIS_LOG_LEVEL=debug

# Set custom cache directory
export POLARIS_CACHE_DIR="/path/to/cache"
```

### Desktop Environment Integration

#### GNOME
```bash
# Add to favorites
gsettings set org.gnome.shell favorite-apps "$(gsettings get org.gnome.shell favorite-apps | sed "s/]/, 'polaris-node-manager.desktop']/")"
```

#### KDE Plasma
```bash
# Pin to taskbar - done through right-click menu in application launcher
```

## 🔧 System Integration

### Systemd Service (Optional)
Create a user service for automatic startup:
```bash
# Create service file
mkdir -p ~/.config/systemd/user
cat > ~/.config/systemd/user/polaris-node-manager.service << EOF
[Unit]
Description=Polaris Node Manager
After=network.target

[Service]
Type=simple
ExecStart=/usr/bin/polaris-node-manager --headless
Restart=always
RestartSec=10

[Install]
WantedBy=default.target
EOF

# Enable and start service
systemctl --user daemon-reload
systemctl --user enable polaris-node-manager.service
systemctl --user start polaris-node-manager.service
```

### Firewall Configuration

#### UFW (Ubuntu/Debian)
```bash
# Allow outbound HTTPS
sudo ufw allow out 443/tcp

# Allow outbound SSH
sudo ufw allow out 22/tcp

# Reload firewall
sudo ufw reload
```

#### Firewalld (Fedora/RHEL/CentOS)
```bash
# Allow outbound HTTPS and SSH
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --reload
```

## 🧹 Maintenance

### Updating the Application

#### Package Installation
```bash
# Ubuntu/Debian
sudo apt update && sudo apt upgrade polaris-node-manager

# Fedora
sudo dnf update polaris-node-manager

# RHEL/CentOS
sudo yum update polaris-node-manager
```

#### AppImage/Portable
Download new version and replace existing files.

### Clearing Data
```bash
# Clear logs
rm -rf ~/.local/share/polaris-node-manager/logs/*

# Clear cache
rm -rf ~/.cache/polaris-node-manager/*

# Reset configuration (caution!)
rm -rf ~/.config/polaris-node-manager/
```

### Backup Configuration
```bash
# Backup user configuration
tar -czf polaris-backup-$(date +%Y%m%d).tar.gz ~/.config/polaris-node-manager/
```

## 🚨 Troubleshooting

### Common Issues

#### Missing Dependencies
```bash
# Ubuntu/Debian
sudo apt install --fix-missing
sudo apt install -f

# Fedora
sudo dnf install glibc gtk3 libnotify

# Check missing libraries
ldd /usr/bin/polaris-node-manager | grep "not found"
```

#### Permission Issues
```bash
# Fix executable permissions
chmod +x ./PolarisNodeManager-2.0.0.AppImage
chmod +x ./polaris-node-manager

# Fix configuration directory permissions
chmod -R 755 ~/.config/polaris-node-manager/
```

#### Display Issues
```bash
# Wayland compatibility
export GDK_BACKEND=wayland

# X11 fallback
export GDK_BACKEND=x11

# HiDPI scaling
export GDK_SCALE=2
export GDK_DPI_SCALE=0.5
```

#### Network Issues
```bash
# Test connectivity
curl -I https://api.bittensor.com

# Check DNS resolution
nslookup polariscloud.ai

# Test SSH connectivity
ssh -T user@your-mining-machine
```

### Debug Mode
```bash
# Run with debug output
POLARIS_DEBUG=true ./polaris-node-manager

# Check system logs
journalctl --user -u polaris-node-manager.service

# Application logs
tail -f ~/.local/share/polaris-node-manager/logs/app.log
```

## 🔄 Uninstallation

### Package Installation
```bash
# Ubuntu/Debian
sudo apt remove polaris-node-manager
sudo apt purge polaris-node-manager  # Remove configuration files

# Fedora/RHEL/CentOS
sudo dnf remove polaris-node-manager
```

### AppImage/Portable
```bash
# Remove application files
rm -f PolarisNodeManager-2.0.0.AppImage
rm -rf polaris-node-manager/

# Remove user data (optional)
rm -rf ~/.config/polaris-node-manager/
rm -rf ~/.local/share/polaris-node-manager/
```

### Clean Uninstall
```bash
# Remove all traces
rm -rf ~/.config/polaris-node-manager/
rm -rf ~/.local/share/polaris-node-manager/
rm -rf ~/.cache/polaris-node-manager/
rm -f ~/.local/share/applications/polaris-node-manager.desktop
```

## 📞 Support

### Linux-Specific Support
- **System Logs**: Use `journalctl` to check system logs
- **Package Manager**: Use your distribution's package manager for dependency issues
- **Desktop Environment**: Check desktop-specific forums for integration issues

### Distribution-Specific Help
- **Ubuntu/Debian**: [Ask Ubuntu](https://askubuntu.com)
- **Fedora**: [Fedora Forums](https://ask.fedoraproject.org)
- **Arch Linux**: [Arch Wiki](https://wiki.archlinux.org)

### Getting Help
- 📧 **Email**: support@polarisnode.com
- 💬 **Discord**: [Join our community](https://discord.gg/polaris)
- 📖 **Documentation**: [Full docs](https://docs.polarisnode.com)
- 🐛 **Issues**: [GitHub Issues](https://github.com/bigideaafrica/polaris_distributions/issues)

## 📋 Command Line Usage

### Available Options
```bash
# Display help
polaris-node-manager --help

# Run with custom configuration
polaris-node-manager --config=/path/to/config.json

# Run in headless mode (no GUI)
polaris-node-manager --headless

# Run with debug logging
polaris-node-manager --debug

# Run with specific log level
polaris-node-manager --log-level=verbose

# Show version information
polaris-node-manager --version
```

### Integration with Scripts
```bash
#!/bin/bash
# Example startup script

# Set environment
export POLARIS_CONFIG_DIR="$HOME/.polaris-config"
export POLARIS_DEBUG=false

# Start application
exec /usr/bin/polaris-node-manager "$@"
```

### 🛠️ Advanced Support Features

#### Built-in Contact Support System
Polaris Node Manager v2 includes a comprehensive support system:

1. **Access Support**: Click the "Contact Support" button in the main interface
2. **Select Machine**: Choose specific machines from the dropdown list (shows machine ID, username, and status)
3. **Describe Issues**: Use the detailed text area to describe problems with each machine
4. **Multiple Queries**: Add multiple support queries for different machines in one request
5. **Attach Screenshots**: Upload screenshots and images to help illustrate issues
6. **Alternative Channels**: Access direct links to Twitter and Discord for additional support

#### Support Request Features
- **Machine-Specific Support**: Target support requests to specific mining machines
- **Comprehensive Details**: Each machine shows GPU info, IP address, and current status
- **Multi-Machine Support**: Handle multiple machine issues in a single support ticket
- **Visual Evidence**: Attach screenshots and images to support requests
- **Real-time Submission**: Send support requests directly from the application

---

**Ready to manage your mining operations on Linux?** Choose your preferred installation method above and start monitoring your mining machines today! 🐧🚀
