# Polaris Node Manager v2.0.0 - Linux

Welcome to the Linux distribution of **Polaris Node Manager v2**! This package provides multiple installation options optimized for different Linux distributions and use cases.

## 📦 Available Downloads

### Package Installers
- **polaris-node-manager_2.0.0_amd64.deb** - For Debian/Ubuntu systems
- **polaris-node-manager_2.0.0_x86_64.rpm** - For RHEL/Fedora/CentOS systems
- **File Size**: ~120MB each
- **Installation**: System package managers
- **Updates**: Through system updates

### Portable Options
- **PolarisNodeManager-2.0.0.AppImage** - Universal Linux application
- **polaris-node-manager-linux-x86_64.tar.gz** - Portable tarball
- **File Size**: ~100MB compressed
- **Installation**: Extract and run
- **Updates**: Manual download required

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

### Method 1: DEB Package (Ubuntu/Debian)

#### Option A: Download and Install
```bash
# Download DEB package
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_amd64.deb"

# Install with dpkg
sudo dpkg -i polaris-node-manager_2.0.0_amd64.deb

# Install dependencies if needed
sudo apt-get install -f
```

#### Option B: One-Line Installation
```bash
# Download and install in one command
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_amd64.deb" -o /tmp/polaris.deb && sudo dpkg -i /tmp/polaris.deb && sudo apt-get install -f
```

### Method 2: RPM Package (Fedora/RHEL/CentOS)

#### Fedora
```bash
# Download RPM package
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_x86_64.rpm"

# Install with dnf
sudo dnf install ./polaris-node-manager_2.0.0_x86_64.rpm
```

#### RHEL/CentOS
```bash
# Download RPM package
curl -L "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager_2.0.0_x86_64.rpm" -o polaris-node-manager.rpm

# Install with yum/dnf
sudo yum install ./polaris-node-manager.rpm
# OR for newer versions
sudo dnf install ./polaris-node-manager.rpm
```

### Method 3: AppImage (Universal)

#### Download and Run
```bash
# Download AppImage
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/PolarisNodeManager-2.0.0.AppImage"

# Make executable
chmod +x PolarisNodeManager-2.0.0.AppImage

# Run the application
./PolarisNodeManager-2.0.0.AppImage
```

#### Desktop Integration (Optional)
```bash
# Create desktop entry
cat > ~/.local/share/applications/polaris-node-manager.desktop << EOF
[Desktop Entry]
Type=Application
Name=Polaris Node Manager
Comment=Mining Machine Management
Exec=$PWD/PolarisNodeManager-2.0.0.AppImage
Icon=polaris-node-manager
Categories=Network;System;
EOF

# Update desktop database
update-desktop-database ~/.local/share/applications/
```

### Method 4: Portable Tarball

#### Extract and Run
```bash
# Download tarball
wget "https://github.com/bigideaafrica/polaris_distributions/raw/main/v2/linux/polaris-node-manager-linux-x86_64.tar.gz"

# Extract
tar -xzf polaris-node-manager-linux-x86_64.tar.gz

# Navigate to directory
cd polaris-node-manager

# Make executable
chmod +x polaris-node-manager

# Run application
./polaris-node-manager
```

## 📂 File Structure

### Package Installation
```
/usr/bin/polaris-node-manager              # Main executable
/usr/share/polaris-node-manager/           # Application resources
/usr/share/applications/                   # Desktop entry
/usr/share/icons/hicolor/                  # Application icons
/usr/share/doc/polaris-node-manager/       # Documentation
```

### AppImage Structure
```
PolarisNodeManager-2.0.0.AppImage          # Self-contained application
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
# Direct execution
./PolarisNodeManager-2.0.0.AppImage

# Background execution
nohup ./PolarisNodeManager-2.0.0.AppImage &
```

### From Portable
```bash
# Navigate to directory and run
cd polaris-node-manager
./polaris-node-manager
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

---

**Ready to manage your mining operations on Linux?** Choose your preferred installation method above and start monitoring your mining machines today! 🐧🚀
