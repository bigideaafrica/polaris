# Polaris Installer v1.0.0

This is the first release of the Polaris Installer application, a tool designed to simplify the setup and management of Polaris mining nodes on the Bittensor network.

## Downloads

- [Windows Installer](./windows/PolarisInstaller-Setup.exe)
- [Linux Installers](./linux/) (DEB, RPM, and tarball available)
- MacOS Installer (Coming Soon)

### Command-Line Download

You can download Polaris Installer directly using command-line tools:

**Windows PowerShell**: (Open PowerShell, not Command Prompt)
```powershell
# Download Windows installer
Invoke-WebRequest -Uri "https://github.com/BANADDA/polaris_distributions/raw/main/v1/windows/PolarisInstaller-Setup.exe" -OutFile "PolarisInstaller-Setup.exe"

# Run the installer after download
Start-Process -FilePath ".\PolarisInstaller-Setup.exe"
```

**Windows Command Prompt (cmd.exe)**:
```cmd
# Download Windows installer
curl -L -o PolarisInstaller-Setup.exe https://github.com/BANADDA/polaris_distributions/raw/main/v1/windows/PolarisInstaller-Setup.exe

# Run the installer after download
start PolarisInstaller-Setup.exe
```

**Linux (Debian/Ubuntu)**:
```bash
# Download DEB package
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_amd64.deb" -o "polaris-installer_1.0.0_amd64.deb"

# Install the package
sudo dpkg -i polaris-installer_1.0.0_amd64.deb
sudo apt-get install -f  # Install dependencies if needed
```

**Linux (Fedora/RHEL/CentOS)**:
```bash
# Download RPM package
curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_x86_64.rpm" -o "polaris-installer_1.0.0_x86_64.rpm"

# Install the package
sudo rpm -i polaris-installer_1.0.0_x86_64.rpm
```

**Linux (Generic)**:
```bash
# Download tarball
wget "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer-linux-x86_64.tar.gz"

# Extract and run
tar -xzf polaris-installer-linux-x86_64.tar.gz
cd polaris-installer
chmod +x polaris-installer
./polaris-installer
```

## Minimum Requirements

### Windows
- Windows 10 or later
- 4GB RAM
- 100MB free disk space
- Internet connection for registration and mining
- Python 3.8+ (included in installer)

### Linux
- Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, etc.)
- 4GB RAM
- 100MB free disk space
- Internet connection for registration and mining
- Python 3.8+ (included in installer)

### System Requirements for Mining
- CPU: 2+ cores recommended
- RAM: 8GB+ recommended
- Storage: 10GB+ free space
- GPU: Optional but recommended for improved mining performance

## Key Features

- **Simplified Registration**: One-click registration process for Polaris mining nodes
- **System Information Detection**: Automatically detects and reports system specifications
- **Network Settings**: Configure network parameters for optimal connection
- **Wallet Management**: Create and manage cryptocurrency wallets
- **Subnet Configuration**: Set up and configure your subnet for mining
- **Real-time Monitoring**: Monitor your mining node's performance with real-time metrics
- **Heartbeat System**: Automatic node health monitoring and reporting

## Installation Instructions

1. Download the appropriate installer for your operating system
2. Run the installer and follow the on-screen instructions
3. Launch Polaris Installer
4. Follow the registration steps to set up your mining node
5. Start mining with the built-in monitoring tools

## Version History

### v1.0.0 (2025-05-17)
- Initial release
- Windows and Linux support
- Basic mining node setup and monitoring
- Registration with Bittensor network
- System information detection and reporting 