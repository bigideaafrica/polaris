# Polaris Node Manager v2.0.2 - Linux Installation Guide

**Enhanced Connection System & Security for Linux**

This guide covers the installation and usage of Polaris Node Manager v2.0.2 on Linux systems, featuring the new API-based connection system and enhanced SSH key management optimized for Linux environments.

## 🆕 Linux-Specific v2.0.2 Features

### Native Linux Integration
- **OpenSSH Compatibility**: Full integration with Linux OpenSSH client and server configurations
- **Systemd Service Support**: Enhanced systemd integration for background operation
- **Distribution Agnostic**: Universal AppImage works across all major Linux distributions
- **Desktop Environment Integration**: Improved integration with GNOME, KDE, XFCE, and other desktop environments

### Enhanced Linux Performance
- **API-Based Connections**: Optimized connection handling leveraging Linux networking stack
- **Process Management**: Better Linux process management and resource allocation
- **Permission Handling**: Improved handling of Linux file permissions and SSH key security
- **Shell Integration**: Enhanced integration with bash, zsh, and other Linux shells

## System Requirements

### Minimum Requirements
- **Distribution**: Any modern Linux distribution (2020+)
  - Ubuntu 20.04+ / Debian 11+
  - Fedora 35+ / CentOS 8+
  - openSUSE 15.3+ / Arch Linux
  - Linux Mint 20+
- **Architecture**: x86_64 (64-bit)
- **RAM**: 4GB minimum (8GB recommended for multi-machine management)
- **Storage**: 500MB free disk space
- **Network**: Stable internet connection

### Required Packages
**Ubuntu/Debian:**
```bash
sudo apt update
sudo apt install -y openssh-client python3 python3-pip curl wget unzip
```

**Fedora/RHEL:**
```bash
sudo dnf install -y openssh-clients python3 python3-pip curl wget unzip
```

**Arch Linux:**
```bash
sudo pacman -S openssh python python-pip curl wget unzip
```

**openSUSE:**
```bash
sudo zypper install openssh-clients python3 python3-pip curl wget unzip
```

### Optional Dependencies
- **Git**: For repository access
- **Desktop Integration**: For .desktop file creation
- **AppImage Launcher**: For better AppImage integration

## Download & Installation

### Method 1: Quick Download (Recommended)

**Download the latest Linux build:**
- **File**: `polaris-node-manager-linux.zip`
- **Size**: 402 MB
- **URL**: [GitHub Releases v2.0.2](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.2)

### Method 2: Command Line Download

```bash
# Create download directory
mkdir -p $HOME/Downloads/polaris-v2.0.2
cd $HOME/Downloads/polaris-v2.0.2

# Download using wget
wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-linux.zip

# Or using curl
curl -L -o polaris-node-manager-linux.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.2/polaris-node-manager-linux.zip

# Extract
unzip polaris-node-manager-linux.zip
cd polaris-node-manager-linux
```

## Installation Process

### Standard Installation (Recommended)

1. **Make AppImage Executable:**
   ```bash
   chmod +x polaris-node-manager.AppImage
   ```

2. **Install System-Wide:**
   ```bash
   # Copy to system binary directory
   sudo cp polaris-node-manager.AppImage /usr/local/bin/polaris-node-manager
   
   # Create symbolic link for easier access
   sudo ln -sf /usr/local/bin/polaris-node-manager /usr/local/bin/polaris
   ```

3. **Create Desktop Entry:**
   ```bash
   # Create desktop entry for menu integration
   cat > ~/.local/share/applications/polaris-node-manager.desktop << EOF
   [Desktop Entry]
   Name=Polaris Node Manager
   Comment=Multi-machine mining rig management
   Exec=/usr/local/bin/polaris-node-manager
   Icon=polaris-node-manager
   Terminal=false
   Type=Application
   Categories=Network;System;
   StartupWMClass=polaris-node-manager
   EOF
   
   # Update desktop database
   update-desktop-database ~/.local/share/applications/
   ```

### User Installation (No Root Required)

```bash
# Create user bin directory
mkdir -p $HOME/.local/bin

# Copy AppImage
cp polaris-node-manager.AppImage $HOME/.local/bin/polaris-node-manager
chmod +x $HOME/.local/bin/polaris-node-manager

# Add to PATH (add to ~/.bashrc or ~/.zshrc)
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

### AppImage Launcher Integration (Optional)

For better AppImage integration on modern Linux systems:

```bash
# Install AppImageLauncher (Ubuntu/Debian)
sudo add-apt-repository ppa:appimagelauncher-team/stable
sudo apt update
sudo apt install appimagelauncher

# For other distributions, download from:
# https://github.com/TheAssassin/AppImageLauncher/releases
```

## Using v2.0.2 Features on Linux

### Setting Up SSH Connections

#### Method 1: Direct Key Input (New in v2.0.2)

1. **Launch Application:**
   ```bash
   # From terminal
   polaris-node-manager
   
   # Or from desktop menu
   # Applications → Network → Polaris Node Manager
   ```

2. **Add New Machine:**
   - Click "Add Machine" button
   - Enter machine details:
     - **Hostname/IP**: Target machine address
     - **Username**: SSH username (e.g., ubuntu, root, your-username)
     - **Port**: SSH port (default: 22)

3. **SSH Key Setup:**
   - **Option A - Direct Paste** (Recommended):
     - Copy your SSH private key content:
       ```bash
       cat ~/.ssh/id_rsa  # or your key file
       ```
     - Paste directly into "SSH Private Key" text area
     - System validates key format automatically
   
   - **Option B - Load from File**:
     - Click "Load Key from File" button
     - Navigate to your key file (usually in `~/.ssh/`)
     - Select appropriate key file

4. **Connect:**
   - Click "Connect" button
   - Monitor connection status in real-time
   - Enhanced error messages guide troubleshooting

#### SSH Key Management on Linux

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

**Generating SSH Keys on Linux:**
```bash
# Generate Ed25519 key (recommended)
ssh-keygen -t ed25519 -C "your-email@example.com" -f ~/.ssh/polaris_key

# Generate RSA key (traditional)
ssh-keygen -t rsa -b 4096 -C "your-email@example.com" -f ~/.ssh/polaris_key

# Set proper permissions
chmod 600 ~/.ssh/polaris_key
chmod 644 ~/.ssh/polaris_key.pub
```

**Copy public key to remote machine:**
```bash
# Method 1: ssh-copy-id (recommended)
ssh-copy-id -i ~/.ssh/polaris_key.pub user@remote-server

# Method 2: Manual copy
cat ~/.ssh/polaris_key.pub | ssh user@remote-server 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

### Linux-Specific Enhanced Features

#### Systemd Service Integration

Create a systemd service for background operation:

```bash
# Create service file
sudo tee /etc/systemd/system/polaris-node-manager.service > /dev/null << EOF
[Unit]
Description=Polaris Node Manager
After=network.target

[Service]
Type=simple
User=$USER
ExecStart=/usr/local/bin/polaris-node-manager --headless
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
EOF

# Enable and start service
sudo systemctl enable polaris-node-manager
sudo systemctl start polaris-node-manager

# Check status
sudo systemctl status polaris-node-manager
```

#### Desktop Environment Integration

**GNOME Integration:**
```bash
# Install GNOME Shell extension support
sudo apt install gnome-shell-extension-manager  # Ubuntu/Debian
sudo dnf install gnome-shell-extension-manager  # Fedora

# Add to GNOME favorites
gsettings set org.gnome.shell favorite-apps "$(gsettings get org.gnome.shell favorite-apps | sed "s/]/, 'polaris-node-manager.desktop']/")"
```

**KDE Integration:**
```bash
# Create KDE service menu entry
mkdir -p ~/.local/share/kservices5/ServiceMenus/
cat > ~/.local/share/kservices5/ServiceMenus/polaris-manager.desktop << EOF
[Desktop Entry]
Type=Service
X-KDE-ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/x-ssh-key;
Actions=manage-with-polaris;

[Desktop Action manage-with-polaris]
Name=Manage with Polaris
Icon=polaris-node-manager
Exec=/usr/local/bin/polaris-node-manager %f
EOF
```

### Linux-Specific Troubleshooting

#### Permission Issues

**Problem**: SSH key permission errors
**Solution**: Fix SSH key permissions

```bash
# Fix SSH directory permissions
chmod 700 ~/.ssh/
chmod 600 ~/.ssh/id_*
chmod 644 ~/.ssh/*.pub
chmod 644 ~/.ssh/authorized_keys
chmod 644 ~/.ssh/known_hosts
```

#### AppImage Execution Issues

**Problem**: AppImage won't run
**Solution**: Check FUSE and permissions

```bash
# Install FUSE (if missing)
sudo apt install fuse libfuse2          # Ubuntu/Debian
sudo dnf install fuse fuse-libs         # Fedora
sudo pacman -S fuse2                    # Arch Linux

# Make executable
chmod +x polaris-node-manager.AppImage

# Run with debug output
./polaris-node-manager.AppImage --appimage-extract-and-run
```

#### Network Connection Issues

**Problem**: API-based connections fail
**Solution**: Check firewall and network settings

```bash
# Check if port 22 is accessible
nc -zv target-server 22

# Check local firewall (UFW)
sudo ufw status
sudo ufw allow 22/tcp

# Check local firewall (firewalld)
sudo firewall-cmd --list-all
sudo firewall-cmd --add-service=ssh --permanent
sudo firewall-cmd --reload

# Check iptables
sudo iptables -L INPUT | grep ssh
```

#### Python Dependencies

**Problem**: Python-related errors
**Solution**: Install Python dependencies

```bash
# Install required Python packages
pip3 install --user paramiko psutil

# For system-wide installation
sudo pip3 install paramiko psutil

# Or use distribution packages
sudo apt install python3-paramiko python3-psutil    # Ubuntu/Debian
sudo dnf install python3-paramiko python3-psutil    # Fedora
```

#### Desktop Integration Issues

**Problem**: Application not appearing in menu
**Solution**: Update desktop database

```bash
# Update desktop database
update-desktop-database ~/.local/share/applications/

# Refresh icon cache
gtk-update-icon-cache ~/.local/share/icons/

# For system-wide installation
sudo update-desktop-database /usr/share/applications/
```

### Performance Optimization for Linux

#### System Tuning

```bash
# Increase file descriptor limits
echo "* soft nofile 65536" | sudo tee -a /etc/security/limits.conf
echo "* hard nofile 65536" | sudo tee -a /etc/security/limits.conf

# Optimize network settings
echo 'net.core.rmem_default = 262144' | sudo tee -a /etc/sysctl.conf
echo 'net.core.wmem_default = 262144' | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

#### Resource Monitoring

```bash
# Monitor Polaris processes
ps aux | grep polaris
htop -p $(pgrep -f polaris)

# Monitor network connections
netstat -tulpn | grep polaris
ss -tulpn | grep polaris

# Monitor system resources
iostat -x 1
iftop -i eth0
```

## Distribution-Specific Notes

### Ubuntu/Debian
- Default SSH service may need to be started: `sudo systemctl enable ssh`
- AppImage may require `libfuse2`: `sudo apt install libfuse2`

### Fedora/RHEL
- SELinux may require configuration for SSH keys
- Use `sudo setsebool -P ssh_sysadm_login on` if needed

### Arch Linux
- Install `openssh` package if not present
- AUR packages available for additional integration

### openSUSE
- YaST can be used for SSH configuration
- Firewall configuration through YaST or firewalld

## Advanced Linux Configuration

### Environment Variables

```bash
# Add to ~/.bashrc or ~/.zshrc
export POLARIS_HOME="$HOME/.config/polaris"
export POLARIS_LOG_LEVEL="info"
export POLARIS_SSH_KEY_PATH="$HOME/.ssh/polaris_key"
```

### Configuration Files

```bash
# Main configuration directory
~/.config/polaris/
├── config.json          # Main configuration
├── machines.json        # Machine configurations
├── logs/               # Application logs
└── ssh_keys/           # Cached SSH keys (encrypted)
```

### Shell Integration

```bash
# Add useful aliases to ~/.bashrc
alias polaris='polaris-node-manager'
alias polaris-logs='tail -f ~/.config/polaris/logs/app.log'
alias polaris-config='cat ~/.config/polaris/config.json | jq .'
```

## Uninstallation

### Complete Removal

```bash
# Remove system installation
sudo rm -f /usr/local/bin/polaris-node-manager
sudo rm -f /usr/local/bin/polaris

# Remove desktop entry
rm -f ~/.local/share/applications/polaris-node-manager.desktop
update-desktop-database ~/.local/share/applications/

# Remove configuration (optional)
rm -rf ~/.config/polaris/
rm -rf ~/.cache/polaris/

# Remove systemd service (if created)
sudo systemctl stop polaris-node-manager
sudo systemctl disable polaris-node-manager
sudo rm -f /etc/systemd/system/polaris-node-manager.service
sudo systemctl daemon-reload
```

## Migration from v2.0.1

v2.0.2 automatically migrates existing Linux configurations:

```bash
# Configuration migration path
~/.config/polaris/v2.0.1/ → ~/.config/polaris/v2.0.2/

# Manual backup (optional)
cp -r ~/.config/polaris/v2.0.1/ ~/.config/polaris/backup-v2.0.1/
```

## Support Resources

### Linux-Specific Debugging

```bash
# Application logs
journalctl -f -u polaris-node-manager  # If running as service
tail -f ~/.config/polaris/logs/app.log

# System logs
dmesg | grep polaris
journalctl --since "1 hour ago" | grep polaris

# Network debugging
tcpdump -i any host target-server and port 22
```

### Getting Help
- **GitHub Issues**: [Linux-specific issues](https://github.com/bigideaafrica/polaris_distributions/issues)
- **In-App Support**: Contact Support feature with machine selection
- **Log Files**: `~/.config/polaris/logs/`

---

**Linux Installation Complete!** You're now ready to use Polaris Node Manager v2.0.2 with enhanced connection system and optimized Linux integration. 