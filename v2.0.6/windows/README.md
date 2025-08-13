# Polaris Node Manager v2.0.6 - Windows

## Installation

### Requirements
- Windows 10 or later (x64)
- .NET Framework 4.7.2 or later (usually pre-installed)

### Download
- **ZIP Package**: `polaris-node-manager-windows-v2.0.6.zip`

### Installation Instructions

1. Download the ZIP package
2. Right-click and select "Extract All..." 
3. Choose your desired installation location
4. Navigate to the extracted folder
5. Run `Polaris Node Manager Setup.exe` as Administrator
6. Follow the installation wizard

### Alternative Portable Installation
If you prefer not to install, you can run the portable version:
1. Extract the ZIP package
2. Navigate to the `win-unpacked` folder
3. Run `Polaris Node Manager.exe`

### What's New in v2.0.6

#### Desktop App Enhancements
- **Compute Resources Screen**: New dedicated interface for managing compute resources
- **API Services Integration**: Enhanced API services management with API key handling (marked "Coming Soon")
- **Template System**: Pre-configured deployment templates including:
  - PolarisLLM
  - CUDA environments  
  - PyTorch
  - TensorFlow
  - Ubuntu VMs
- **One-click Deployment**: Streamlined deployment workflow with real-time status tracking
- **Improved Resource Management**: Enhanced UI with real-time filtering and visual indicators

#### Template Features
- 8+ curated container images from Docker Hub
- Custom template creation capabilities
- Public repository template support
- Enhanced deployment processing for remote machines
- Template database integration

#### UI/UX Improvements
- Native Windows 10/11 design language
- Green highlighting for owned resources
- Fixed header with inline statistics
- Windows-native toast notifications for deployment progress
- Improved modal interfaces with comprehensive information display

#### Access Methods Enhancement
- Comprehensive modal interface displaying:
  - SSH credentials
  - Connection details
  - Container information
  - Rental duration
- Enhanced copy-to-clipboard functionality

#### Deployment Workflow
- One-click deployment with status tracking
- Progress notifications using Windows notification system
- Real-time filtering capabilities
- Template processing for remote machine deployment

### Windows-Specific Features
- Native Windows notifications
- High DPI display support
- Windows Defender SmartScreen compatibility
- Auto-updater integration

### Firewall Configuration
The application may request firewall permissions for network operations. Please allow access for full functionality.

### Troubleshooting
Common issues and solutions:
1. **Installation blocked**: Run the installer as Administrator
2. **App won't start**: Ensure Windows 10/11 x64 and .NET Framework 4.7.2+
3. **Firewall warnings**: Allow network access for cloud connectivity
4. **Performance issues**: Check Windows Update for latest drivers

### Support
For technical support and documentation, visit the main project repository.

---
**Note**: This version includes significant improvements to the desktop application interface and deployment capabilities, optimized for Windows 10/11.
