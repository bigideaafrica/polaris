# Polaris Node Manager v2.0.4 - Linux

**Security-Enhanced Release for Modern Linux Distributions**

This release introduces critical security enhancements including updated server public keys, endpoint security hardening, and comprehensive TLS 1.3 implementation for Linux users.

## 🔒 Security Enhancements in v2.0.4

### Linux-Specific Security Features
- **System Certificate Store Integration**: Seamless integration with system CA certificates
- **SELinux/AppArmor Compatibility**: Enhanced security context support
- **systemd Integration**: Proper service management and security sandboxing
- **Keyring Support**: Integration with GNOME Keyring and KDE Wallet
- **Secure File Permissions**: Proper file permissions and ownership management

### Updated Security Components
- **RSA-4096 Server Keys**: Enhanced cryptographic protection
- **OpenSSL 3.0+ Support**: Latest cryptographic library support
- **Certificate Pinning**: Automatic certificate validation and pinning
- **Encrypted Data Storage**: AES-256-GCM encryption for all sensitive data
- **Mandatory Access Control**: Support for SELinux and AppArmor policies

## Download Information

### File Details
- **Filename**: `polaris-node-manager-linux-v2.0.4.zip`
- **Size**: ~418MB (increased from v2.0.3 due to security libraries)
- **Format**: ZIP archive containing AppImage and additional files
- **Architecture**: x86_64 (AMD64) - Universal Linux build
- **AppImage Version**: polaris-node-manager-linux-v2.0.4.AppImage

### Checksum Verification
```bash
# Verify file integrity
sha256sum polaris-node-manager-linux-v2.0.4.zip
# Expected: [SHA256 hash will be provided with release]

# Verify AppImage integrity
sha256sum polaris-node-manager-linux-v2.0.4.AppImage
# Expected: [SHA256 hash will be provided with release]
```

## System Requirements

### Minimum Requirements (Updated for v2.0.4)
- **OS**: Ubuntu 20.04 LTS+, Fedora 35+, Debian 11+, or equivalent
- **Kernel**: Linux 5.4+ (Linux 5.15+ recommended for enhanced security)
- **RAM**: 4GB minimum (8GB recommended for secure multi-machine management)
- **Storage**: 750MB free disk space (increased for security libraries)
- **Network**: TLS 1.3 capable internet connection
- **Permissions**: sudo privileges for initial setup and certificate management

### Security Requirements
- **OpenSSL**: Version 3.0 or later for TLS 1.3 support
- **CA Certificates**: Up-to-date certificate authority bundle
- **Firewall**: iptables or firewalld for network security
- **AppArmor/SELinux**: Security module support (optional but recommended)

### System Dependencies
```bash
# Ubuntu/Debian dependencies
sudo apt update
sudo apt install ca-certificates openssl libssl3 curl wget unzip

# Fedora/RHEL dependencies  
sudo dnf install ca-certificates openssl curl wget unzip

# Arch Linux dependencies
sudo pacman -S ca-certificates openssl curl wget unzip
```

### Optional Security Components
- **GNOME Keyring**: For secure credential storage in GNOME environments
- **KDE Wallet**: For secure credential storage in KDE environments
- **Hardware Security Module**: For enterprise-grade key storage
- **Yubikey/FIDO2**: For hardware-based authentication

## Installation Methods

### Method 1: Direct Download and Run
```bash
# Download the release
wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-linux-v2.0.4.zip

# Extract the archive
unzip polaris-node-manager-linux-v2.0.4.zip

# Navigate to extracted directory
cd polaris-node-manager-linux-v2.0.4

# Make AppImage executable
chmod +x polaris-node-manager-linux-v2.0.4.AppImage

# Run the application
./polaris-node-manager-linux-v2.0.4.AppImage
```

### Method 2: cURL Installation
```bash
# Download using cURL
curl -L -o polaris-v2.0.4-linux.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-linux-v2.0.4.zip

# Extract and setup
unzip polaris-v2.0.4-linux.zip
cd polaris-node-manager-linux-v2.0.4
chmod +x polaris-node-manager-linux-v2.0.4.AppImage

# Run application
./polaris-node-manager-linux-v2.0.4.AppImage
```

### Method 3: Installation Script
```bash
#!/bin/bash
# Polaris Node Manager v2.0.4 Installation Script

# Set variables
RELEASE_URL="https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-linux-v2.0.4.zip"
INSTALL_DIR="$HOME/Applications/polaris-node-manager"
APPIMAGE_NAME="polaris-node-manager-linux-v2.0.4.AppImage"

# Create installation directory
mkdir -p "$INSTALL_DIR"
cd "$INSTALL_DIR"

# Download and extract
echo "Downloading Polaris Node Manager v2.0.4..."
wget "$RELEASE_URL" -O polaris-v2.0.4.zip

echo "Extracting application..."
unzip polaris-v2.0.4.zip
chmod +x "$APPIMAGE_NAME"

# Create desktop entry
echo "Creating desktop entry..."
cat > ~/.local/share/applications/polaris-node-manager.desktop << EOF
[Desktop Entry]
Type=Application
Name=Polaris Node Manager
Comment=Mining Machine Management Application
Exec=$INSTALL_DIR/$APPIMAGE_NAME
Icon=$INSTALL_DIR/polaris-icon.png
Categories=Utility;Network;
EOF

echo "Installation complete! Run: $INSTALL_DIR/$APPIMAGE_NAME"
```

## Linux-Specific Security Configuration

### Certificate Store Integration
The application integrates with the system certificate store:

```bash
# Update system certificates (Ubuntu/Debian)
sudo apt update && sudo apt install ca-certificates
sudo update-ca-certificates

# Update system certificates (Fedora/RHEL)
sudo dnf update ca-certificates

# Update system certificates (Arch Linux)
sudo pacman -S ca-certificates
sudo update-ca-trust
```

### SELinux Configuration
For SELinux-enabled systems:

```bash
# Check SELinux status
sestatus

# Allow AppImage execution (if needed)
sudo setsebool -P allow_execstack 1

# Create custom SELinux policy for Polaris (advanced)
# Contact support for enterprise SELinux policy templates
```

### AppArmor Configuration
For AppArmor-enabled systems:

```bash
# Check AppArmor status
sudo aa-status

# Create AppArmor profile for Polaris (optional)
sudo tee /etc/apparmor.d/polaris-node-manager << EOF
#include <tunables/global>

profile polaris-node-manager /home/*/Applications/polaris-node-manager/*.AppImage flags=(unconfined) {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/ssl_certs>
  
  # Allow network access
  network inet stream,
  network inet6 stream,
  
  # Allow file access
  /home/*/Applications/polaris-node-manager/** r,
  /home/*/.config/polaris-node-manager/** rw,
  /home/*/.local/share/polaris-node-manager/** rw,
}
EOF

# Load the profile
sudo apparmor_parser -r /etc/apparmor.d/polaris-node-manager
```

## Desktop Integration

### AppImage Integration
```bash
# Install AppImage integration tools (optional)
# Ubuntu/Debian
sudo apt install appimaged

# Fedora
sudo dnf install appimaged

# Manual desktop integration
./polaris-node-manager-linux-v2.0.4.AppImage --appimage-extract-and-run --install
```

### System Service (Advanced)
Create a systemd user service for background operation:

```bash
# Create user service directory
mkdir -p ~/.config/systemd/user

# Create service file
cat > ~/.config/systemd/user/polaris-node-manager.service << EOF
[Unit]
Description=Polaris Node Manager Background Service
After=network-online.target
Wants=network-online.target

[Service]
Type=simple
ExecStart=/home/%i/Applications/polaris-node-manager/polaris-node-manager-linux-v2.0.4.AppImage --background
Restart=always
RestartSec=10

[Install]
WantedBy=default.target
EOF

# Enable and start service
systemctl --user enable polaris-node-manager.service
systemctl --user start polaris-node-manager.service
```

## Running the Application

### Application Directories
```bash
# Configuration directory
~/.config/polaris-node-manager/
├── config.json          # Main configuration (encrypted)
├── certificates/         # Certificate cache
├── logs/                 # Application logs
└── security/            # Security keys and tokens

# Data directory
~/.local/share/polaris-node-manager/
├── machines/            # Machine configurations
├── performance/         # Performance data
└── updates/            # Auto-update downloads
```

### File Permissions
The application automatically sets secure file permissions:

```bash
# Configuration files (600 - owner read/write only)
chmod 600 ~/.config/polaris-node-manager/config.json

# Certificate files (400 - owner read only)
chmod 400 ~/.config/polaris-node-manager/certificates/*

# Log files (644 - owner read/write, others read)
chmod 644 ~/.config/polaris-node-manager/logs/*
```

## Linux-Specific Features

### Keyring Integration
The application integrates with Linux keyring systems:

```bash
# GNOME Keyring integration
# Credentials stored in: gnome-keyring-daemon
# Access via: secret-tool lookup service polaris-node-manager

# KDE Wallet integration  
# Credentials stored in: kdewallet
# Access via: kwallet-query kdewallet
```

### System Integration
- **D-Bus Integration**: For desktop notifications and system integration
- **XDG Compliance**: Follows XDG Base Directory Specification
- **Systemd Integration**: Proper service management and logging
- **Network Manager**: Integration with NetworkManager for connection status

## Troubleshooting

### Common Issues and Solutions

#### 1. "AppImage won't run"
**Symptoms**: AppImage fails to execute
**Solutions**:
```bash
# Check AppImage permissions
ls -la polaris-node-manager-linux-v2.0.4.AppImage

# Make executable if needed
chmod +x polaris-node-manager-linux-v2.0.4.AppImage

# Check FUSE support
lsmod | grep fuse
# If not loaded: sudo modprobe fuse

# Install FUSE if missing
sudo apt install fuse libfuse2  # Ubuntu/Debian
sudo dnf install fuse fuse-libs # Fedora
```

#### 2. "Certificate validation errors"
**Symptoms**: SSL/TLS connection failures
**Solutions**:
```bash
# Update certificate bundle
sudo apt update && sudo apt install ca-certificates
sudo update-ca-certificates

# Check certificate store
ls -la /etc/ssl/certs/ca-certificates.crt

# Test TLS connection manually
openssl s_client -connect polariscloud.ai:443 -servername polariscloud.ai -tls1_3
```

#### 3. "Permission denied errors"
**Symptoms**: Cannot access configuration files
**Solutions**:
```bash
# Check file ownership
ls -la ~/.config/polaris-node-manager/

# Fix ownership if needed
sudo chown -R $USER:$USER ~/.config/polaris-node-manager/
sudo chown -R $USER:$USER ~/.local/share/polaris-node-manager/

# Reset permissions
chmod -R 700 ~/.config/polaris-node-manager/
chmod -R 755 ~/.local/share/polaris-node-manager/
```

#### 4. "Network connectivity issues"
**Symptoms**: Cannot connect to Polaris servers
**Solutions**:
```bash
# Check network connectivity
ping -c 4 polariscloud.ai

# Test HTTPS connectivity
curl -I https://polariscloud.ai

# Check firewall rules
sudo iptables -L OUTPUT | grep -i drop
sudo ufw status # if using UFW

# Allow HTTPS traffic
sudo ufw allow out 443/tcp
```

#### 5. "OpenSSL/TLS version issues"
**Symptoms**: TLS handshake failures
**Solutions**:
```bash
# Check OpenSSL version
openssl version

# Update OpenSSL
sudo apt update && sudo apt install openssl libssl3  # Ubuntu/Debian
sudo dnf update openssl openssl-libs                 # Fedora

# Check TLS 1.3 support
openssl ciphers -tls1_3
```

### System Information for Support
```bash
#!/bin/bash
# Generate system information for support

echo "=== System Information ==="
echo "Distribution: $(lsb_release -d | cut -f2)"
echo "Kernel: $(uname -r)"
echo "Architecture: $(uname -m)"
echo "OpenSSL Version: $(openssl version)"

echo "=== Network Information ==="
echo "DNS Servers: $(cat /etc/resolv.conf | grep nameserver)"
echo "Default Gateway: $(ip route | grep default)"

echo "=== Security Information ==="
echo "SELinux Status: $(sestatus 2>/dev/null || echo 'Not available')"
echo "AppArmor Status: $(sudo aa-status 2>/dev/null | head -1 || echo 'Not available')"

echo "=== Certificate Information ==="
echo "CA Certificates: $(ls -la /etc/ssl/certs/ca-certificates.crt)"
echo "System Certificate Count: $(ls /etc/ssl/certs/*.pem 2>/dev/null | wc -l)"

echo "=== Application Information ==="
echo "AppImage Location: $(find . -name '*.AppImage' -type f)"
echo "Config Directory: $(ls -la ~/.config/polaris-node-manager/ 2>/dev/null || echo 'Not found')"
```

## Performance Optimization

### Linux-Specific Optimizations
- **Memory Management**: Utilizes Linux memory management for optimal performance
- **I/O Scheduling**: Optimized for Linux I/O schedulers (CFQ, deadline, noop)
- **CPU Affinity**: Automatic CPU affinity optimization for multi-core systems
- **Network Stack**: Optimized for Linux TCP/IP stack

### Resource Usage
- **Memory**: ~85MB base usage (+20MB for security features on Linux)
- **CPU**: <1% idle usage, 2-5% during active operations
- **Disk**: Minimal I/O, primarily for logging and configuration
- **Network**: Efficient connection pooling, typically <1MB/hour background traffic

## Security Best Practices

### Linux System Security
1. **Keep System Updated**: Regularly update your Linux distribution
2. **Use Package Manager**: Install security updates via package manager
3. **Enable Firewall**: Configure iptables or firewalld
4. **Regular Security Scans**: Use tools like rkhunter, chkrootkit
5. **File Integrity**: Monitor system files with AIDE or similar tools

### Application Security
1. **Verify Downloads**: Always verify checksums and signatures
2. **Secure Permissions**: Maintain proper file permissions
3. **Regular Updates**: Keep application updated to latest version
4. **Monitor Logs**: Regularly check application logs for anomalies
5. **Network Monitoring**: Monitor network connections with netstat/ss

## Distribution-Specific Notes

### Ubuntu/Debian
```bash
# Additional security packages
sudo apt install rkhunter chkrootkit aide

# Automatic security updates
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

### Fedora/RHEL/CentOS
```bash
# SELinux tools
sudo dnf install policycoreutils-python-utils

# Automatic security updates
sudo dnf install dnf-automatic
sudo systemctl enable dnf-automatic.timer
```

### Arch Linux
```bash
# Security tools
sudo pacman -S rkhunter aide

# Automatic updates (use with caution)
yay -S arch-update
```

## Enterprise Deployment

### Ansible Playbook
```yaml
---
- name: Deploy Polaris Node Manager v2.0.4
  hosts: linux_workstations
  become: yes
  vars:
    polaris_version: "2.0.4"
    polaris_url: "https://github.com/bigideaafrica/polaris_distributions/releases/download/v{{ polaris_version }}/polaris-node-manager-linux-v{{ polaris_version }}.zip"
    
  tasks:
    - name: Install dependencies
      package:
        name: "{{ item }}"
        state: present
      loop:
        - ca-certificates
        - openssl
        - curl
        - wget
        - unzip
        
    - name: Download Polaris Node Manager
      get_url:
        url: "{{ polaris_url }}"
        dest: "/tmp/polaris-v{{ polaris_version }}.zip"
        
    - name: Extract application
      unarchive:
        src: "/tmp/polaris-v{{ polaris_version }}.zip"
        dest: "/opt/"
        remote_src: yes
        
    - name: Set permissions
      file:
        path: "/opt/polaris-node-manager-linux-v{{ polaris_version }}"
        mode: '0755'
        recurse: yes
```

### Docker Deployment
```dockerfile
FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && apt-get install -y \
    ca-certificates \
    openssl \
    libssl3 \
    curl \
    wget \
    unzip \
    fuse \
    libfuse2

# Download and install Polaris Node Manager
RUN wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-linux-v2.0.4.zip \
    && unzip polaris-node-manager-linux-v2.0.4.zip \
    && chmod +x polaris-node-manager-linux-v2.0.4.AppImage

# Create non-root user
RUN useradd -m -s /bin/bash polaris

# Set working directory
WORKDIR /home/polaris
USER polaris

# Run application
CMD ["./polaris-node-manager-linux-v2.0.4.AppImage", "--no-sandbox"]
```

## Support Information

### Linux-Specific Support Channels
- **Linux Issues**: linux-support@polariscloud.ai
- **Enterprise Support**: enterprise@polariscloud.ai
- **Security Issues**: security@polariscloud.ai

### Community Support
- **GitHub Discussions**: [polaris_distributions/discussions](https://github.com/bigideaafrica/polaris_distributions/discussions)
- **Discord**: [#linux-support](https://discord.gg/polaris-mining)
- **Reddit**: [r/PolarisNodeManager](https://reddit.com/r/PolarisNodeManager)

## Version Information

- **Version**: 2.0.4
- **Linux Build**: 2.0.4-linux-x86_64
- **Security Level**: Enhanced
- **Support Until**: January 2025
- **Minimum Kernel**: Linux 5.4
- **Recommended Kernel**: Linux 5.15 or later

---

**Security Notice**: This version contains critical security updates. Upgrading from previous versions is strongly recommended. Always download from official sources and verify file integrity before installation. 