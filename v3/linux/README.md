# Polaris Node Manager v3.0.0 - Linux

Linux distribution of Polaris Node Manager v3.0.0 with Ubuntu-optimized builds and comprehensive Linux distribution support.

## 📦 Available Downloads

### Ubuntu Latest Build
- **File**: `ubuntu-latest-build.zip`
- **Architecture**: x86_64 (AMD64)
- **Format**: Universal ZIP containing AppImage and installation scripts
- **Size**: ~150MB (compressed)

## 🔧 Installation

### Quick Installation (Recommended)

1. **Download and Extract**:
   ```bash
   wget -O polaris-v3-linux.zip [download-url]
   unzip polaris-v3-linux.zip
   cd polaris-v3-linux/
   ```

2. **Run Installation Script**:
   ```bash
   chmod +x install.sh
   sudo ./install.sh
   ```

3. **Launch Application**:
   ```bash
   polaris-node-manager
   # Or from Applications menu: "Polaris Node Manager"
   ```

### Manual Installation

1. **Extract the ZIP file**:
   ```bash
   unzip ubuntu-latest-build.zip
   ```

2. **Make AppImage executable**:
   ```bash
   chmod +x Polaris-Node-Manager-v3.0.0.AppImage
   ```

3. **Run directly** (portable mode):
   ```bash
   ./Polaris-Node-Manager-v3.0.0.AppImage
   ```

4. **Install system-wide** (optional):
   ```bash
   sudo cp Polaris-Node-Manager-v3.0.0.AppImage /usr/local/bin/polaris-node-manager
   sudo chmod +x /usr/local/bin/polaris-node-manager
   ```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: Ubuntu 20.04 LTS or later (other distributions supported)
- **Architecture**: x86_64 (AMD64)
- **RAM**: 8GB minimum (16GB recommended)
- **Storage**: 2GB free disk space
- **Display**: X11 or Wayland display server
- **Network**: Broadband internet connection

### Recommended Requirements
- **OS**: Ubuntu 22.04 LTS or later
- **RAM**: 16GB or more
- **CPU**: 4+ cores (8+ recommended for cloud operations)
- **Storage**: 10GB+ SSD storage
- **GPU**: NVIDIA/AMD GPU with latest drivers (for AI workloads)

## 🐧 Distribution Compatibility

### Officially Supported
- **Ubuntu**: 20.04 LTS, 22.04 LTS, 23.04+
- **Debian**: 11 (Bullseye), 12 (Bookworm)
- **Fedora**: 37, 38, 39+
- **CentOS Stream**: 9
- **RHEL**: 9+

### Community Tested
- **openSUSE**: Leap 15.4+, Tumbleweed
- **Arch Linux**: Rolling release
- **Manjaro**: Latest stable
- **Linux Mint**: 21+
- **Pop!_OS**: 22.04+

## 🔧 Dependencies

### Required Dependencies
The installation script will automatically install these if missing:

```bash
# Core dependencies
sudo apt update
sudo apt install -y \
    curl \
    wget \
    unzip \
    ca-certificates \
    gnupg \
    lsb-release

# Container runtime
sudo apt install -y docker.io docker-compose

# Development tools (optional)
sudo apt install -y \
    git \
    python3 \
    python3-pip \
    nodejs \
    npm
```

### Docker Installation
For optimal container management, install Docker:

```bash
# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker
```

## 🚀 Quick Start

1. **Launch Polaris Node Manager**:
   ```bash
   polaris-node-manager
   ```

2. **Complete Initial Setup**:
   - Follow the setup wizard
   - Configure cloud provider credentials
   - Set up your first compute resource

3. **Deploy Your First Template**:
   - Browse the template library
   - Select a pre-configured template
   - Deploy with one-click

## 🔒 Security Considerations

### Firewall Configuration
Open required ports for Polaris services:

```bash
# SSH access
sudo ufw allow 22/tcp

# Polaris API
sudo ufw allow 8080/tcp

# Container ports (as needed)
sudo ufw allow 3000:9000/tcp

# Enable firewall
sudo ufw enable
```

### SELinux (RHEL/CentOS/Fedora)
If using SELinux, configure appropriate policies:

```bash
# Set SELinux to permissive for Docker
sudo setsebool -P container_manage_cgroup on
sudo setsebool -P virt_use_execmem on
```

## 🐛 Troubleshooting

### Common Issues

**AppImage won't run**:
```bash
# Install FUSE if missing
sudo apt install fuse libfuse2

# Or run with --appimage-extract-and-run
./Polaris-Node-Manager-v3.0.0.AppImage --appimage-extract-and-run
```

**Docker permission denied**:
```bash
# Add user to docker group and restart
sudo usermod -aG docker $USER
sudo systemctl restart docker
# Log out and back in, or run: newgrp docker
```

**Network connectivity issues**:
```bash
# Check DNS resolution
nslookup api.polaris.bigideaafrica.com

# Test network connectivity
curl -I https://api.polaris.bigideaafrica.com/health
```

### Log Files
Application logs are stored in:
- **System logs**: `/var/log/polaris/`
- **User logs**: `~/.local/share/polaris/logs/`
- **Container logs**: `docker logs polaris-node-manager`

## 🔄 Updates

### Automatic Updates
Polaris v3.0.0 includes automatic update checking:
- Updates are checked on startup
- Notifications appear when updates are available
- One-click update process

### Manual Updates
```bash
# Download new version
wget -O polaris-v3-latest.zip [latest-download-url]

# Backup current installation
cp ~/.config/polaris/config.json ~/polaris-config-backup.json

# Install new version
unzip polaris-v3-latest.zip
sudo ./install.sh

# Restore configuration if needed
cp ~/polaris-config-backup.json ~/.config/polaris/config.json
```

## 📚 Additional Resources

- **Documentation**: [docs.polaris.bigideaafrica.com/linux](https://docs.polaris.bigideaafrica.com/linux)
- **Linux-specific guides**: [guides.polaris.bigideaafrica.com/linux](https://guides.polaris.bigideaafrica.com/linux)
- **Community forum**: [community.polaris.bigideaafrica.com](https://community.polaris.bigideaafrica.com)

## 📞 Support

For Linux-specific issues:
- **GitHub Issues**: [Report a bug](https://github.com/bigideaafrica/polaris_distributions/issues)
- **Community Support**: [Linux Discussion Forum](https://community.polaris.bigideaafrica.com/c/linux)
- **Documentation**: [Linux Installation Guide](https://docs.polaris.bigideaafrica.com/installation/linux)

---

**Build Information**:
- Build Date: Latest development build
- Compiler: GCC 11.x with glibc 2.31+
- Package Format: AppImage (portable) + DEB installer
- Dependencies: Bundled with minimal system requirements
