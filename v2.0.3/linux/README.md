# Polaris Node Manager v2.0.3 - Linux

**Advanced Real-Time Monitoring System for Linux**

This guide covers installation and setup of Polaris Node Manager v2.0.3 on Linux systems, featuring comprehensive monitoring capabilities optimized for Linux environments.

## 📥 Download & Installation

### Quick Installation

1. **Download the Package**
   ```
   File: polaris-node-manager-linux.zip
   Size: ~402MB
   ```

2. **Extract and Install**
   ```bash
   # Extract the archive
   unzip polaris-node-manager-linux.zip
   cd polaris-node-manager-linux
   
   # Make executable and run
   chmod +x polaris-node-manager.AppImage
   ./polaris-node-manager.AppImage
   ```

### Installation Methods

#### AppImage (Recommended)
```bash
# Download and run directly
wget https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.3/polaris-node-manager-linux.zip
unzip polaris-node-manager-linux.zip
chmod +x polaris-node-manager.AppImage
./polaris-node-manager.AppImage
```

#### DEB Package (Ubuntu/Debian)
```bash
# If DEB package is included
sudo dpkg -i polaris-node-manager_2.0.3_amd64.deb
sudo apt-get install -f  # Fix dependencies if needed
```

#### RPM Package (CentOS/RHEL/Fedora)
```bash
# If RPM package is included
sudo rpm -ivh polaris-node-manager-2.0.3-1.x86_64.rpm
# or
sudo dnf install polaris-node-manager-2.0.3-1.x86_64.rpm
```

#### Portable Tarball
```bash
# Extract and run portable version
tar -xzf polaris-node-manager-linux-portable.tar.gz
cd polaris-node-manager
./polaris-node-manager
```

## 🚀 New Monitoring Features in v2.0.3

### **Linux-Specific Monitoring Enhancements**

#### **Connection Monitoring**
- **iptables/netfilter Integration**: Real-time firewall rule monitoring and validation
- **Network Interface Monitoring**: Comprehensive monitoring of all network interfaces
- **SystemD Network Service**: Integration with systemd-networkd and NetworkManager
- **Port Binding Validation**: Checks for port conflicts and availability

#### **Authentication Monitoring**
- **SSH Daemon Integration**: Direct monitoring of sshd service status and configuration
- **PAM Authentication**: Integration with Linux PAM system for authentication monitoring
- **Key-based Authentication**: Advanced SSH key validation and permission checking
- **SELinux/AppArmor Support**: Security context monitoring for enhanced systems

#### **Performance Monitoring (PoW)**
- **Linux Performance Counters**: Integration with perf subsystem for detailed metrics
- **GPU Monitoring**: Native support for NVIDIA (nvidia-ml) and AMD (ROCm) GPU monitoring
- **CPU Frequency Scaling**: Monitoring of CPU governor and frequency scaling
- **Memory Management**: Detailed Linux memory subsystem monitoring (RSS, VSZ, swap usage)
- **Load Average Tracking**: Real-time system load monitoring and trending

#### **Docker Environment Monitoring**
- **Docker Daemon Integration**: Direct communication with Docker daemon via socket
- **Container Runtime Monitoring**: Support for Docker, Podman, and containerd
- **Systemd Service Integration**: Monitoring of Docker systemd service status
- **cgroups Monitoring**: Resource usage monitoring via Linux cgroups

## 🖥️ Linux System Requirements

### **Minimum Requirements**
- **Operating System**: Linux kernel 3.10+ (recommended 4.0+)
- **Distribution**: Ubuntu 18.04+, CentOS 7+, Debian 9+, Fedora 28+, or equivalent
- **Architecture**: x86_64 (amd64)
- **RAM**: 4GB minimum, 8GB recommended
- **Storage**: 1GB free space for application and monitoring data
- **Network**: Stable internet connection with outbound HTTPS access

### **Recommended for Optimal Monitoring**
- **Modern Distribution**: Ubuntu 20.04+, CentOS 8+, or equivalent
- **Kernel**: Linux 5.0+ for advanced monitoring features
- **RAM**: 16GB for monitoring multiple high-performance machines
- **SSD Storage**: For faster monitoring data processing and caching
- **Dedicated Network**: Ethernet connection for stable monitoring connectivity

### **For Mining Machines (Linux)**
- **Docker**: Latest Docker CE or Docker from distribution repositories
- **SSH Server**: OpenSSH server properly configured and running
- **Firewall**: iptables or firewalld properly configured
- **System Monitoring Tools**: htop, iotop, nethogs for enhanced monitoring

## 🔧 Linux-Specific Setup

### **1. Install Required Dependencies**

#### Ubuntu/Debian
```bash
# Update package list
sudo apt update

# Install required packages
sudo apt install -y openssh-server docker.io curl wget unzip

# Enable and start services
sudo systemctl enable ssh docker
sudo systemctl start ssh docker

# Add user to docker group
sudo usermod -aG docker $USER
```

#### CentOS/RHEL/Fedora
```bash
# Install required packages
sudo dnf install -y openssh-server docker curl wget unzip
# or for older systems: sudo yum install -y openssh-server docker curl wget unzip

# Enable and start services
sudo systemctl enable sshd docker
sudo systemctl start sshd docker

# Add user to docker group
sudo usermod -aG docker $USER
```

### **2. Configure SSH Server**

#### Basic SSH Configuration
```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Recommended settings:
# Port 22
# PermitRootLogin no
# PubkeyAuthentication yes
# PasswordAuthentication yes
# ChallengeResponseAuthentication no

# Restart SSH service
sudo systemctl restart sshd
```

#### Generate SSH Key Pair (if needed)
```bash
# Generate SSH key pair
ssh-keygen -t rsa -b 4096 -C "polaris-mining@$(hostname)"

# Copy public key to mining machines
ssh-copy-id user@mining-machine-ip
```

### **3. Configure Firewall**

#### Using iptables
```bash
# Allow SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow Docker
sudo iptables -A INPUT -p tcp --dport 2375:2376 -j ACCEPT

# Save rules (Ubuntu/Debian)
sudo iptables-save > /etc/iptables/rules.v4
```

#### Using firewalld (CentOS/RHEL/Fedora)
```bash
# Allow SSH
sudo firewall-cmd --permanent --add-service=ssh

# Allow Docker
sudo firewall-cmd --permanent --add-port=2375-2376/tcp

# Reload firewall
sudo firewall-cmd --reload
```

## 📊 Linux Monitoring Dashboard

### **Linux-Specific Status Indicators**

#### **System Health Panel**
- **Kernel Version**: Monitors kernel version and available updates
- **System Uptime**: Tracks system stability and uptime records
- **Disk Health**: SMART monitoring for all storage devices
- **Journal Monitoring**: systemd journal monitoring for critical events

#### **Process Monitoring**
- **Process Tree**: Real-time process hierarchy monitoring
- **Resource Usage**: Per-process CPU, memory, and I/O monitoring
- **Zombie Processes**: Detection and monitoring of zombie processes
- **Process Limits**: ulimit and systemd resource limit monitoring

#### **Network Monitoring**
- **Interface Statistics**: Detailed statistics for all network interfaces
- **Routing Table**: Real-time routing table monitoring
- **DNS Resolution**: DNS performance and resolution monitoring
- **Network Namespaces**: Container network namespace monitoring

#### **Storage Monitoring**
- **Filesystem Usage**: Real-time filesystem usage and inode monitoring
- **Mount Points**: Monitoring of all mount points and filesystem types
- **I/O Statistics**: Detailed disk I/O statistics and queue monitoring
- **RAID Status**: Hardware and software RAID status monitoring

## 🛠️ Linux-Specific Troubleshooting

### **Common Linux Issues**

#### **Connection Problems**
- **Firewall Blocking**: Check iptables/firewalld rules
  ```bash
  sudo iptables -L -n
  sudo firewall-cmd --list-all
  ```
- **SSH Service Issues**: Check SSH daemon status
  ```bash
  sudo systemctl status sshd
  sudo journalctl -u sshd -f
  ```
- **Network Configuration**: Validate network interface configuration
  ```bash
  ip addr show
  ip route show
  ```

#### **Authentication Issues**
- **SSH Key Permissions**: Fix SSH key file permissions
  ```bash
  chmod 700 ~/.ssh
  chmod 600 ~/.ssh/id_rsa
  chmod 644 ~/.ssh/id_rsa.pub ~/.ssh/authorized_keys
  ```
- **SELinux Issues**: Check SELinux context for SSH keys
  ```bash
  ls -Z ~/.ssh/
  restorecon -R ~/.ssh/
  ```
- **PAM Configuration**: Check PAM SSH configuration
  ```bash
  sudo nano /etc/pam.d/sshd
  ```

#### **Performance Issues**
- **System Load**: Monitor system load and identify bottlenecks
  ```bash
  top
  htop
  iotop
  ```
- **Memory Issues**: Check memory usage and swap activity
  ```bash
  free -h
  cat /proc/meminfo
  vmstat 1
  ```
- **CPU Throttling**: Check for thermal throttling
  ```bash
  cat /proc/cpuinfo | grep MHz
  sensors
  ```

#### **Docker Issues**
- **Docker Daemon**: Check Docker daemon status
  ```bash
  sudo systemctl status docker
  sudo journalctl -u docker -f
  ```
- **Docker Permissions**: Fix Docker group permissions
  ```bash
  sudo usermod -aG docker $USER
  newgrp docker
  ```
- **Storage Driver Issues**: Check Docker storage driver
  ```bash
  docker info | grep "Storage Driver"
  ```

### **Linux System Monitoring Tools**

#### **Built-in Monitoring Commands**
```bash
# System information
uname -a
lscpu
lsmem
lsblk

# Process monitoring
ps aux
pstree
pgrep polaris

# Network monitoring
ss -tulpn
netstat -tulpn
lsof -i

# System resources
df -h
du -sh /*
iostat 1
```

## 🔒 Linux Security Features

### **Enhanced Security Monitoring**
- **SELinux/AppArmor Integration**: Security policy monitoring and enforcement
- **Audit Subsystem**: Linux audit framework integration for security monitoring
- **File Integrity Monitoring**: Real-time file system change monitoring
- **Process Monitoring**: Advanced process monitoring with security context

### **Credential Security**
- **Keyring Integration**: Linux keyring support for secure credential storage
- **SSH Agent**: Integration with ssh-agent for key management
- **Encrypted Storage**: File system encryption support (LUKS, eCryptfs)
- **Access Control**: POSIX ACL and extended attributes support

## 📈 Performance Optimization for Linux

### **Linux-Specific Optimizations**
- **Kernel Parameters**: Automatic tuning of kernel parameters for mining performance
- **CPU Affinity**: Process CPU affinity optimization for mining tasks
- **Memory Management**: Linux memory management tuning (transparent huge pages, swappiness)
- **I/O Scheduling**: I/O scheduler optimization for mining workloads

### **Monitoring Efficiency**
- **perf Integration**: Linux perf subsystem for low-overhead monitoring
- **eBPF Support**: Extended Berkeley Packet Filter for advanced monitoring
- **cgroups Monitoring**: Efficient resource monitoring via Linux control groups
- **systemd Integration**: Native systemd service monitoring and management

## 🆘 Linux Support Resources

### **Linux-Specific Help**
- **Man Pages**: Comprehensive manual pages for all Linux components
- **System Logs**: Guide to reading system logs and journal entries
- **Performance Analysis**: Using Linux performance analysis tools
- **Debugging**: Linux debugging techniques and tools

### **Common Linux Commands**
```bash
# Check SSH service
sudo systemctl status sshd
sudo ss -tlnp | grep :22

# Test network connectivity
ping -c 4 mining-machine-ip
nc -zv mining-machine-ip 22

# Check Docker
sudo systemctl status docker
docker version
docker ps

# Monitor system performance
top
htop
iotop
nethogs
```

## 🔄 Upgrading from Previous Versions

### **From v2.0.2 on Linux**
- **In-Place Upgrade**: Replace AppImage or reinstall package
- **Configuration Migration**: Linux configuration files automatically migrated
- **Service Preservation**: systemd services updated without interruption
- **Permission Maintenance**: File permissions and ownership preserved

### **Linux-Specific Migration Notes**
- **systemd Services**: Service files updated automatically
- **Firewall Rules**: iptables/firewalld rules preserved
- **User Groups**: Docker and SSH group memberships maintained
- **Cron Jobs**: Scheduled tasks preserved during upgrade

## 🐧 Distribution-Specific Notes

### **Ubuntu/Debian**
- **Snap Package**: Available via Ubuntu Snap Store
- **PPA Repository**: Official PPA for easy updates
- **AppArmor**: Enhanced security with AppArmor profiles

### **CentOS/RHEL/Fedora**
- **RPM Package**: Native RPM packaging for system integration
- **SELinux**: Full SELinux policy support
- **systemd**: Native systemd integration

### **Arch Linux**
- **AUR Package**: Available in Arch User Repository
- **Rolling Release**: Continuous updates with latest features

---

**Polaris Node Manager v2.0.3 for Linux** provides comprehensive mining management with deep Linux system integration. Take advantage of native Linux monitoring capabilities for optimal mining performance and system visibility.

For Linux-specific support, check system logs using `journalctl` and use the extensive Linux monitoring tools available on your distribution. 