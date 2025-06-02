# Polaris Installer for Windows (v1.0.0)

This folder contains the Windows distribution of Polaris Installer v1.0.0.

## Installation Options

1. **Easy Install**: Run [PolarisInstaller-Setup.exe](./PolarisInstaller-Setup.exe) for a guided installation
2. **Portable Version**: Use the [portable](./portable/) directory for a no-install option
3. **Command-Line Download**: 
   
   Using PowerShell (run PowerShell as administrator):
   ```powershell
   # Download the installer
   Invoke-WebRequest -Uri "https://github.com/bigideaafrica/polaris_distributions/raw/main/v1/windows/PolarisInstaller-Setup.exe" -OutFile "PolarisInstaller-Setup.exe"
   
   # Run the installer after download
   Start-Process -FilePath ".\PolarisInstaller-Setup.exe"
   ```
   
   Using Command Prompt (cmd.exe):
   ```cmd
   # Download the installer
   curl -L -o PolarisInstaller-Setup.exe https://github.com/bigideaafrica/polaris_distributions/raw/main/v1/windows/PolarisInstaller-Setup.exe
   
   # Run the installer after download
   start PolarisInstaller-Setup.exe
   ```

## Installation Steps After Download

1. Once the download completes, double-click the `PolarisInstaller-Setup.exe` file or use the command shown above to run it
2. If a security warning appears, click "Run" or "Yes" to continue
3. Follow the on-screen instructions in the installer wizard
4. Choose your preferred installation location or accept the default
5. Select any additional components you want to install
6. Wait for the installation to complete
7. Click "Finish" to complete the installation

The installer will create a desktop shortcut and a Start menu entry for easy access.

## System Requirements

- Windows 10 or later (64-bit)
- 4GB RAM minimum (8GB recommended)
- 100MB disk space
- Internet connection
- Administrator privileges for installation

## Common Issues and Solutions

### Installation Issues
- **Error about missing DLL files**: Install the latest Microsoft Visual C++ Redistributable
- **Windows Defender warning**: This may occur because the application is not widely distributed yet. You can safely add an exception.

### Registration Issues
- **Connection failed**: Ensure your internet connection is stable
- **GPU not detected**: Update your graphics drivers to the latest version

## Support

For support, please visit our [GitHub repository](https://github.com/PolarisNetwork/polaris-installer) or join our [Discord community](https://discord.gg/polarisnetwork). 