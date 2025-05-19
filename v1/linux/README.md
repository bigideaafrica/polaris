# Polaris Installer for Linux (v1.0.0)

This folder contains the Linux distribution of Polaris Installer v1.0.0.

## Installation Options

1. **Debian-based distributions**: Install [polaris-installer_1.0.0_amd64.deb](./polaris-installer_1.0.0_amd64.deb) using `sudo dpkg -i polaris-installer_1.0.0_amd64.deb`
2. **RPM-based distributions**: Install [polaris-installer_1.0.0_x86_64.rpm](./polaris-installer_1.0.0_x86_64.rpm) using `sudo rpm -i polaris-installer_1.0.0_x86_64.rpm`
3. **Other Linux distributions**: Extract [polaris-installer-linux-x86_64.tar.gz](./polaris-installer-linux-x86_64.tar.gz) and run the executable
4. **Command-Line Download**:

   **Debian/Ubuntu**:
   ```bash
   # Download the DEB package
   curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_amd64.deb" -o "polaris-installer_1.0.0_amd64.deb"
   
   # Install the package
   sudo dpkg -i polaris-installer_1.0.0_amd64.deb
   sudo apt-get install -f  # Install dependencies if needed
   
   # Launch the application
   polaris-installer
   ```
   
   **Fedora/RHEL/CentOS**:
   ```bash
   # Download the RPM package
   curl -L "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer_1.0.0_x86_64.rpm" -o "polaris-installer_1.0.0_x86_64.rpm"
   
   # Install the package
   sudo rpm -i polaris-installer_1.0.0_x86_64.rpm
   
   # Launch the application
   polaris-installer
   ```
   
   **Other Linux Distributions**:
   ```bash
   # Download the tarball
   wget "https://github.com/BANADDA/polaris_distributions/raw/main/v1/linux/polaris-installer-linux-x86_64.tar.gz"
   
   # Extract the archive
   tar -xzf polaris-installer-linux-x86_64.tar.gz
   
   # Enter the directory
   cd polaris-installer
   
   # Make the executable runnable
   chmod +x polaris-installer
   
   # Run the application
   ./polaris-installer
   ```

## Installation Steps After Download

### For DEB Package (Debian/Ubuntu):
1. Once downloaded, open a terminal in the download directory
2. Run `sudo dpkg -i polaris-installer_1.0.0_amd64.deb` to install the package
3. If there are dependency issues, run `sudo apt-get install -f` to resolve them
4. The installer will be added to your applications menu
5. You can also launch it from the terminal by typing `polaris-installer`

### For RPM Package (Fedora/RHEL/CentOS):
1. Once downloaded, open a terminal in the download directory
2. Run `sudo rpm -i polaris-installer_1.0.0_x86_64.rpm` to install the package
3. The installer will be added to your applications menu
4. You can also launch it from the terminal by typing `polaris-installer`

### For Tarball (Other Linux Distributions):
1. Once downloaded, open a terminal in the download directory
2. Run `tar -xzf polaris-installer-linux-x86_64.tar.gz` to extract the archive
3. Navigate to the extracted directory with `cd polaris-installer`
4. Make the application executable with `chmod +x polaris-installer`
5. Run the application with `./polaris-installer`

After launching the application:
1. The Polaris Installer will guide you through the setup process
2. Configure your network settings for optimal connection
3. Set up your wallet for mining operations
4. Configure your mining parameters
5. Start mining with the built-in monitoring tools

## System Requirements

- Modern Linux distribution (Ubuntu 20.04+, Fedora 35+, etc.)
- 4GB RAM minimum (8GB recommended)
- 100MB disk space
- Internet connection
- sudo privileges for installation (for .deb and .rpm packages)

## Common Issues and Solutions

### Installation Issues
- **Missing dependencies**: Run `sudo apt install -y libgtk-3-0 libxcb-cursor0` (Debian/Ubuntu) or equivalent for your distribution
- **Permission denied**: Ensure the executable has run permissions with `chmod +x polaris-installer`
- **Package conflicts**: If you get conflicts when installing, try `sudo apt --fix-broken install` (Debian/Ubuntu) or `sudo dnf install --allowerasing` (Fedora)

### Registration Issues
- **Connection failed**: Ensure your internet connection is stable
- **GPU not detected**: Verify your GPU drivers are properly installed and up to date
- **Wallet creation fails**: Check your storage space and try again

## Support

For support, please visit our [GitHub repository](https://github.com/PolarisNetwork/polaris-installer) or join our [Discord community](https://discord.gg/polarisnetwork) 