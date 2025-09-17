# Polaris Node Manager v3.0.1 - Linux

Linux distribution of Polaris Node Manager v3.0.1 with advanced container orchestration, AI-powered optimization, and comprehensive multi-distribution support.

## 📦 Available Downloads

### Ubuntu Latest Build
- **File**: `ubuntu-latest-build.zip`
- **Architecture**: x86_64 (AMD64) with ARM64 support
- **Format**: Universal ZIP containing AppImage, DEB package, and installation scripts
- **Size**: ~165MB (compressed)
- **Compatibility**: Ubuntu 20.04+ and most modern Linux distributions

## 🔧 Installation Options

### Option 1: Quick Installation Script (Recommended)

```bash
# Download and extract
wget -O polaris-v3.0.1-linux.zip [download-url]
unzip polaris-v3.0.1-linux.zip
cd polaris-v3.0.1-linux/

# Run installation script
chmod +x install.sh
sudo ./install.sh

# Launch application
polaris-node-manager
```

### Option 2: DEB Package Installation

```bash
# Extract the ZIP file
unzip ubuntu-latest-build.zip

# Install DEB package
sudo dpkg -i polaris-node-manager_3.0.1_amd64.deb

# Install dependencies if needed
sudo apt-get install -f

# Launch from applications menu or command line
polaris-node-manager
```

### Option 3: AppImage (Portable)

```bash
# Extract and make executable
unzip ubuntu-latest-build.zip
chmod +x Polaris-Node-Manager-v3.0.1.AppImage

# Run directly (portable mode)
./Polaris-Node-Manager-v3.0.1.AppImage

# Optional: Install system-wide
sudo cp Polaris-Node-Manager-v3.0.1.AppImage /usr/local/bin/polaris-node-manager
sudo chmod +x /usr/local/bin/polaris-node-manager
```

### Option 4: Manual Installation

```bash
# Extract all files
unzip ubuntu-latest-build.zip
cd polaris-v3.0.1/

# Copy binaries
sudo cp bin/* /usr/local/bin/
sudo chmod +x /usr/local/bin/polaris*

# Copy desktop files
sudo cp share/applications/*.desktop /usr/share/applications/
sudo cp share/icons/hicolor/*/apps/* /usr/share/icons/hicolor/*/apps/

# Update desktop database
sudo update-desktop-database
sudo gtk-update-icon-cache /usr/share/icons/hicolor/
```

## 🖥️ System Requirements

### Minimum Requirements
- **OS**: Ubuntu 20.04 LTS or equivalent (see compatibility list below)
- **Architecture**: x86_64 (AMD64) - ARM64 support available
- **Kernel**: Linux 5.4 or later
- **RAM**: 16GB minimum (32GB recommended for enterprise workloads)
- **Storage**: 10GB free disk space (SSD recommended)
- **CPU**: 4 cores minimum (8+ cores recommended)
- **Network**: Broadband internet connection with stable connectivity

### Recommended Requirements
- **OS**: Ubuntu 22.04 LTS or later
- **RAM**: 32GB or more
- **CPU**: 8+ cores (Intel Xeon/AMD EPYC for enterprise)
- **Storage**: 50GB+ NVMe SSD storage
- **GPU**: NVIDIA RTX 3060 or better (for AI workloads)
- **Network**: Gigabit ethernet connection

## 🐧 Distribution Compatibility

### Tier 1 Support (Officially Tested)
- **Ubuntu**: 20.04 LTS, 22.04 LTS, 23.04, 23.10
- **Debian**: 11 (Bullseye), 12 (Bookworm), 13 (Trixie)
- **Red Hat Enterprise Linux**: 8, 9
- **CentOS Stream**: 8, 9
- **Fedora**: 37, 38, 39, 40
- **SUSE Linux Enterprise**: 15 SP4, 15 SP5

### Tier 2 Support (Community Tested)
- **openSUSE**: Leap 15.4+, Tumbleweed
- **Arch Linux**: Rolling release
- **Manjaro**: Latest stable releases
- **Linux Mint**: 21+
- **Pop!_OS**: 22.04+
- **Elementary OS**: 7+
- **Zorin OS**: 16+

### Tier 3 Support (Basic Compatibility)
- **Alpine Linux**: 3.17+
- **Gentoo**: Latest stable
- **NixOS**: 22.11+
- **Void Linux**: Latest
- **Clear Linux**: Latest

## 🔧 Prerequisites and Dependencies

### Essential Dependencies

The installation script will automatically install these if missing:

```bash
# Update package lists
sudo apt update

# Core system dependencies
sudo apt install -y \
    curl \
    wget \
    unzip \
    ca-certificates \
    gnupg \
    lsb-release \
    software-properties-common \
    apt-transport-https

# Development tools
sudo apt install -y \
    build-essential \
    git \
    python3 \
    python3-pip \
    nodejs \
    npm

# Container runtime
sudo apt install -y \
    docker.io \
    docker-compose-plugin \
    containerd

# Kubernetes tools
sudo apt install -y \
    kubectl \
    helm

# Monitoring tools
sudo apt install -y \
    htop \
    iotop \
    nethogs \
    ncdu
```

### Docker Installation (Recommended)

For optimal container management, install Docker from official repository:

```bash
# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package index
sudo apt update

# Install Docker Engine
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add user to docker group
sudo usermod -aG docker $USER
newgrp docker

# Enable and start Docker service
sudo systemctl enable docker
sudo systemctl start docker

# Verify installation
docker --version
docker compose version
```

### Kubernetes Setup (Optional)

```bash
# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Install Helm
curl https://baltocdn.com/helm/signing.asc | gpg --dearmor | sudo tee /usr/share/keyrings/helm.gpg > /dev/null
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/helm.gpg] https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
sudo apt update
sudo apt install helm

# Install k9s (optional but recommended)
curl -sS https://webinstall.dev/k9s | bash
```

## 🚀 First-Time Setup

### 1. Launch Polaris Node Manager

```bash
# From command line
polaris-node-manager

# Or from applications menu
# Search for "Polaris Node Manager"

# Check if service is running
systemctl --user status polaris-node-manager
```

### 2. Complete Setup Wizard

1. **System Check**: Verify all dependencies are installed
2. **Cloud Provider Configuration**:
   ```bash
   # AWS CLI setup
   aws configure
   
   # Azure CLI setup
   az login
   
   # Google Cloud CLI setup
   gcloud auth login
   gcloud config set project YOUR_PROJECT_ID
   ```

3. **Container Runtime Configuration**:
   ```bash
   # Test Docker connectivity
   docker run hello-world
   
   # Configure Docker for Polaris
   polaris docker configure
   
   # Test Kubernetes connectivity (if available)
   kubectl cluster-info
   ```

4. **AI Features Setup**:
   ```bash
   # Enable AI optimization
   polaris ai enable
   
   # Configure AI models
   polaris ai setup-models
   
   # Test AI functionality
   polaris ai test
   ```

### 3. Linux-Specific Configuration

```bash
# Configure systemd service
polaris service install --user
systemctl --user enable polaris-node-manager
systemctl --user start polaris-node-manager

# Configure firewall (if ufw is active)
polaris firewall configure

# Set up log rotation
polaris logs configure-rotation

# Configure resource limits
polaris system configure-limits
```

## 🛡️ Security Configuration

### Firewall Setup

```bash
# Configure UFW (Ubuntu Firewall)
sudo ufw enable

# Allow SSH access
sudo ufw allow 22/tcp

# Allow Polaris API
sudo ufw allow 8080/tcp

# Allow container ports range
sudo ufw allow 3000:9000/tcp

# Allow Kubernetes API (if using K8s)
sudo ufw allow 6443/tcp

# Check firewall status
sudo ufw status verbose
```

### SELinux Configuration (RHEL/CentOS/Fedora)

```bash
# Check SELinux status
sestatus

# Configure SELinux for containers
sudo setsebool -P container_manage_cgroup on
sudo setsebool -P virt_use_execmem on

# Create custom SELinux policy for Polaris (if needed)
sudo semanage port -a -t http_port_t -p tcp 8080
```

### AppArmor Configuration (Ubuntu/Debian)

```bash
# Check AppArmor status
sudo aa-status

# Configure AppArmor profile for Polaris
sudo cp /usr/share/polaris/apparmor/polaris-node-manager /etc/apparmor.d/
sudo apparmor_parser -r /etc/apparmor.d/polaris-node-manager
```

## 🐳 Advanced Container Management

### Docker Configuration

```bash
# Configure Docker daemon for Polaris
sudo tee /etc/docker/daemon.json > /dev/null <<EOF
{
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "10m",
    "max-file": "3"
  },
  "storage-driver": "overlay2",
  "exec-opts": ["native.cgroupdriver=systemd"],
  "live-restore": true,
  "userland-proxy": false,
  "experimental": true,
  "metrics-addr": "127.0.0.1:9323"
}
EOF

# Restart Docker service
sudo systemctl restart docker

# Verify configuration
docker system info
```

### Kubernetes Integration

```bash
# Install local Kubernetes cluster (kind)
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create local cluster for development
kind create cluster --name polaris-dev

# Configure kubectl context
kubectl cluster-info --context kind-polaris-dev

# Install Polaris operator
polaris k8s install-operator

# Deploy sample workload
polaris k8s deploy --template webapp --cluster kind-polaris-dev
```

### Container Registry Setup

```bash
# Set up local container registry
docker run -d \
  -p 5000:5000 \
  --restart=always \
  --name registry \
  registry:2

# Configure Polaris to use local registry
polaris registry add local --url http://localhost:5000

# Test registry connectivity
polaris registry test local
```

## 📊 Monitoring and Observability

### System Monitoring

```bash
# Install monitoring tools
sudo apt install -y \
    prometheus \
    grafana \
    node-exporter \
    cadvisor

# Configure Prometheus for Polaris
polaris monitoring setup-prometheus

# Start monitoring stack
polaris monitoring start

# Access monitoring dashboards
# Grafana: http://localhost:3000
# Prometheus: http://localhost:9090
```

### Log Management

```bash
# Configure centralized logging
polaris logs setup-centralized

# View real-time logs
polaris logs tail --follow

# Search logs
polaris logs search --query "error" --since "1h"

# Export logs
polaris logs export --format json --output /tmp/polaris-logs.json
```

## 🔧 Performance Optimization

### System Tuning

```bash
# Optimize system for container workloads
echo 'vm.max_map_count=262144' | sudo tee -a /etc/sysctl.conf
echo 'fs.file-max=1000000' | sudo tee -a /etc/sysctl.conf
echo 'net.core.somaxconn=32768' | sudo tee -a /etc/sysctl.conf

# Apply changes
sudo sysctl -p

# Configure resource limits
sudo tee /etc/security/limits.d/polaris.conf > /dev/null <<EOF
polaris soft nofile 1000000
polaris hard nofile 1000000
polaris soft nproc 1000000
polaris hard nproc 1000000
EOF
```

### Storage Optimization

```bash
# Set up storage optimization
polaris storage optimize

# Configure SSD-specific optimizations
if [[ $(lsblk -d -o name,rota | grep -v NAME | awk '{print $2}') == "0" ]]; then
    echo "SSD detected, applying optimizations..."
    sudo systemctl enable fstrim.timer
    sudo systemctl start fstrim.timer
fi

# Configure Docker storage optimization
sudo tee /etc/docker/daemon.json > /dev/null <<EOF
{
  "storage-driver": "overlay2",
  "storage-opts": [
    "overlay2.override_kernel_check=true"
  ]
}
EOF
```

## 🔄 Updates and Maintenance

### Automatic Updates

```bash
# Enable automatic updates
polaris updates enable-auto

# Configure update schedule
polaris updates schedule --time "02:00" --day "sunday"

# Check update status
polaris updates status
```

### Manual Updates

```bash
# Check for updates
polaris updates check

# Download updates
polaris updates download

# Install updates
sudo polaris updates install

# Rollback if needed
sudo polaris updates rollback
```

### Maintenance Tasks

```bash
# System health check
polaris system health-check

# Clean up unused resources
polaris system cleanup

# Backup configuration
polaris backup create --location /backup/polaris/

# Restore from backup
polaris backup restore --location /backup/polaris/latest/

# Generate system report
polaris system report --output /tmp/polaris-report.html
```

## 🐛 Troubleshooting

### Common Issues

**AppImage won't run**:
```bash
# Install FUSE if missing
sudo apt install fuse libfuse2

# Or run with extraction method
./Polaris-Node-Manager-v3.0.1.AppImage --appimage-extract-and-run

# Check AppImage integrity
./Polaris-Node-Manager-v3.0.1.AppImage --appimage-help
```

**Docker permission denied**:
```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Restart Docker service
sudo systemctl restart docker

# Log out and back in, or run:
newgrp docker

# Test Docker access
docker run hello-world
```

**Port conflicts**:
```bash
# Check port usage
sudo netstat -tulpn | grep :8080

# Kill process using port
sudo fuser -k 8080/tcp

# Or configure Polaris to use different port
polaris config set api.port 8081
```

**Network connectivity issues**:
```bash
# Test DNS resolution
nslookup api.polaris.bigideaafrica.com

# Test network connectivity
curl -I https://api.polaris.bigideaafrica.com/health

# Check firewall rules
sudo ufw status verbose

# Test container networking
docker run --rm --network host alpine ping -c 3 google.com
```

### Performance Issues

**High memory usage**:
```bash
# Check memory usage
free -h
ps aux --sort=-%mem | head -20

# Configure memory limits
polaris config set resources.memory.limit "16GB"

# Enable memory optimization
polaris optimize memory
```

**Slow container operations**:
```bash
# Check Docker storage driver
docker info | grep "Storage Driver"

# Optimize Docker storage
sudo systemctl stop docker
sudo rm -rf /var/lib/docker/tmp/*
sudo systemctl start docker

# Check disk I/O
sudo iotop -a
```

### Log Analysis

```bash
# View application logs
journalctl --user -u polaris-node-manager -f

# View system logs
sudo journalctl -u docker -f

# Check kernel logs
sudo dmesg | tail -50

# Analyze logs with polaris tools
polaris logs analyze --level error --since "1h"
```

## 📚 Linux-Specific Resources

### Documentation
- **Linux Installation Guide**: [docs.polaris.bigideaafrica.com/linux](https://docs.polaris.bigideaafrica.com/linux)
- **Container Management**: [docs.polaris.bigideaafrica.com/containers](https://docs.polaris.bigideaafrica.com/containers)
- **Kubernetes Integration**: [docs.polaris.bigideaafrica.com/kubernetes](https://docs.polaris.bigideaafrica.com/kubernetes)
- **Security Best Practices**: [docs.polaris.bigideaafrica.com/security/linux](https://docs.polaris.bigideaafrica.com/security/linux)

### Community Resources
- **Linux Users Forum**: [community.polaris.bigideaafrica.com/c/linux](https://community.polaris.bigideaafrica.com/c/linux)
- **Docker Integration**: [community.polaris.bigideaafrica.com/c/docker](https://community.polaris.bigideaafrica.com/c/docker)
- **Kubernetes Discussions**: [community.polaris.bigideaafrica.com/c/kubernetes](https://community.polaris.bigideaafrica.com/c/kubernetes)

### Scripts and Tools
- **Installation Scripts**: [github.com/bigideaafrica/polaris-linux-scripts](https://github.com/bigideaafrica/polaris-linux-scripts)
- **Monitoring Templates**: [github.com/bigideaafrica/polaris-monitoring](https://github.com/bigideaafrica/polaris-monitoring)
- **Automation Tools**: [github.com/bigideaafrica/polaris-automation](https://github.com/bigideaafrica/polaris-automation)

## 📞 Linux Support

### Linux-Specific Support Channels
- **Linux Technical Support**: linux-support@polaris.bigideaafrica.com
- **Container Support**: containers-support@polaris.bigideaafrica.com
- **Kubernetes Support**: k8s-support@polaris.bigideaafrica.com
- **Enterprise Linux Support**: enterprise-linux@polaris.bigideaafrica.com

### Distribution-Specific Support
- **Ubuntu/Debian**: debian-support@polaris.bigideaafrica.com
- **RHEL/CentOS/Fedora**: redhat-support@polaris.bigideaafrica.com
- **SUSE**: suse-support@polaris.bigideaafrica.com
- **Arch Linux**: arch-support@polaris.bigideaafrica.com

---

**Build Information**:
- **Build Date**: Latest development build
- **Compiler**: GCC 11.x with glibc 2.31+ compatibility
- **Target Architecture**: x86_64 (AMD64) with ARM64 support
- **Package Formats**: AppImage (portable), DEB, RPM, TAR.GZ
- **Dependencies**: Minimal system dependencies with bundled runtime
- **Container Runtime**: Docker 24.0+, containerd 1.6+, Podman 4.0+

**Note**: For the best experience on Linux, we recommend using a recent LTS distribution with the latest kernel and container runtime. The AI features work best with NVIDIA GPUs and CUDA 11.8+ drivers.
