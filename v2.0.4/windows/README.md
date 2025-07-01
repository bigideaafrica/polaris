# Polaris Node Manager v2.0.4 - Windows

**Security-Enhanced Release for Windows 10 Build 20348 and Later**

This release introduces critical security enhancements including updated server public keys, endpoint security hardening, and comprehensive TLS 1.3 implementation for Windows users.

## 🔒 Security Enhancements in v2.0.4

### Windows-Specific Security Features
- **Windows Certificate Store Integration**: Seamless integration with Windows Certificate Store
- **Windows Defender SmartScreen Compatibility**: Code-signed executable for enhanced trust
- **DPAPI Integration**: Data Protection API for secure credential storage
- **Windows Hello Support**: Biometric authentication where available
- **UAC Elevation**: Proper User Account Control integration for secure operations

### Updated Security Components
- **RSA-4096 Server Keys**: Enhanced cryptographic protection
- **TLS 1.3 Support**: Requires Windows 10 Build 20348+ for full TLS 1.3 support
- **Certificate Pinning**: Automatic certificate validation and pinning
- **Encrypted Data Storage**: AES-256-GCM encryption for all sensitive data
- **Rate Limiting Protection**: Advanced protection against abuse

## Download Information

### File Details
- **Filename**: `polaris-node-manager-windows-v2.0.4.zip`
- **Size**: ~185MB (increased from v2.0.3 due to security libraries)
- **Format**: ZIP archive containing portable application
- **Architecture**: x64 (64-bit) - Universal Windows build
- **Digital Signature**: Code-signed with Extended Validation certificate

### Checksum Verification
```powershell
# Verify file integrity (PowerShell)
Get-FileHash polaris-node-manager-windows-v2.0.4.zip -Algorithm SHA256
# Expected: [SHA256 hash will be provided with release]
```

## System Requirements

### Minimum Requirements (Updated for v2.0.4)
- **OS**: Windows 10 Build 20348 or later (Windows 11 recommended)
- **RAM**: 4GB minimum (8GB recommended for secure multi-machine management)  
- **Storage**: 750MB free disk space (increased for security libraries)
- **Network**: TLS 1.3 capable internet connection
- **Permissions**: Administrator privileges for initial setup and certificate management

### Security Requirements
- **Windows Update**: Current Windows Update status for latest TLS support
- **Certificate Store**: Access to Windows Certificate Store
- **Windows Defender**: Windows Defender or compatible antivirus (whitelist may be required)
- **Firewall**: Outbound HTTPS (443) access required
- **TPM**: TPM 2.0 chip recommended for hardware-based security

### Optional Components
- **Windows Hello**: For biometric authentication (requires compatible hardware)
- **Hardware Security Module**: For enterprise-grade key storage
- **Group Policy**: For enterprise deployment and security policies

## Installation Methods

### Method 1: Command Prompt Installation
```cmd
:: Download using curl (available in Windows 10+)
curl -L -o polaris-v2.0.4-windows.zip https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-windows-v2.0.4.zip

:: Extract using built-in tar (Windows 10+)
tar -xf polaris-v2.0.4-windows.zip

:: Navigate to extracted folder
cd polaris-node-manager-windows-v2.0.4

:: Run the application
"Polaris Node Manager.exe"
```

### Method 2: PowerShell Installation (Recommended)
```powershell
# Set execution policy (if needed)
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Download the release
$url = "https://github.com/bigideaafrica/polaris_distributions/releases/download/v2.0.4/polaris-node-manager-windows-v2.0.4.zip"
$output = "polaris-v2.0.4-windows.zip"
Invoke-WebRequest -Uri $url -OutFile $output

# Verify download (optional but recommended)
Get-FileHash $output -Algorithm SHA256

# Extract the archive
Expand-Archive -Path $output -DestinationPath "." -Force

# Navigate to the application directory
Set-Location "polaris-node-manager-windows-v2.0.4"

# Run the application
Start-Process "Polaris Node Manager.exe"
```

### Method 3: Manual Download
1. Visit [Releases Page](https://github.com/bigideaafrica/polaris_distributions/releases/tag/v2.0.4)
2. Download `polaris-node-manager-windows-v2.0.4.zip`
3. Right-click the downloaded file and select "Extract All..."
4. Navigate to the extracted folder
5. Double-click `Polaris Node Manager.exe` to launch

## Windows-Specific Security Configuration

### Windows Defender SmartScreen
When first running the application, Windows Defender SmartScreen may display a warning:

**If you see "Windows protected your PC":**
1. Click "More info"
2. Click "Run anyway"
3. The application will be remembered for future runs

### Windows Certificate Store Setup
The application automatically installs necessary certificates:

```powershell
# Verify certificate installation (PowerShell as Administrator)
Get-ChildItem -Path Cert:\LocalMachine\Root | Where-Object {$_.Subject -like "*polariscloud*"}
```

### Firewall Configuration
Ensure Windows Firewall allows outbound HTTPS connections:

```powershell
# Check firewall rules (PowerShell as Administrator)
Get-NetFirewallRule -DisplayName "*Polaris*" -Direction Outbound
```

### User Account Control (UAC)
The application properly handles UAC elevation:
- Initial certificate installation requires Administrator privileges
- Normal operation runs with standard user privileges
- Automatic elevation prompts appear when necessary

## Running the Application

### First-Time Setup
1. **Launch Application**: Double-click `Polaris Node Manager.exe`
2. **Certificate Installation**: Approve certificate installation when prompted
3. **Windows Hello Setup**: Configure biometric authentication (optional)
4. **Firewall Permissions**: Allow network access when prompted
5. **Initial Security Check**: Application performs automatic security validation

### Normal Operation
- **Desktop Shortcut**: Available after first successful launch
- **Start Menu Entry**: Automatically created in Start Menu
- **System Tray**: Application minimizes to system tray when closed
- **Auto-Update**: Automatic security updates (requires Administrator approval)

### Application Directories
```
%LOCALAPPDATA%\Polaris Node Manager\
├── config\           # Configuration files (encrypted)
├── logs\             # Application logs
├── certificates\     # Certificate cache
├── temp\             # Temporary files
└── updates\          # Auto-update downloads
```

## Windows-Specific Features

### Integration Features
- **Windows Credential Manager**: Secure credential storage
- **Windows Task Scheduler**: Background update checks
- **Windows Event Log**: Security event logging
- **Windows Performance Toolkit**: Resource monitoring integration

### Security Features
- **Code Integrity**: Application files protected by Windows Code Integrity
- **ASLR/DEP**: Address Space Layout Randomization and Data Execution Prevention
- **Control Flow Guard**: Enhanced exploit protection
- **Windows Defender ATP**: Integration with Windows Defender Advanced Threat Protection

## Troubleshooting

### Common Issues and Solutions

#### 1. "Application won't start"
**Symptoms**: Application fails to launch, no error message
**Solutions**:
```cmd
:: Check if .NET Framework is installed
reg query "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" /v Release

:: Run Windows System File Checker
sfc /scannow

:: Check Windows Update status
Get-WindowsUpdate -Online
```

#### 2. "Certificate validation failed"
**Symptoms**: Security errors, connection failures
**Solutions**:
```powershell
# Update Windows certificates
Get-WindowsUpdate -Online -Install -AcceptAll

# Reset certificate store (as Administrator)
certlm.msc
# Navigate to Trusted Root Certification Authorities, remove old Polaris certificates

# Clear certificate cache
Remove-Item "$env:LOCALAPPDATA\Polaris Node Manager\certificates\*" -Force
```

#### 3. "Windows Defender blocking application"
**Symptoms**: Application deleted or quarantined
**Solutions**:
1. Open Windows Security
2. Go to "Virus & threat protection"
3. Click "Manage settings" under "Virus & threat protection settings"
4. Add exclusion for the Polaris Node Manager folder
5. Restore application from quarantine if needed

#### 4. "TLS handshake failed"
**Symptoms**: Network connection errors, API failures
**Solutions**:
```powershell
# Check TLS 1.3 support
[Net.ServicePointManager]::SecurityProtocol
# Should include Tls13

# Enable TLS 1.3 if not available (requires Windows 10 20348+)
# Update Windows to latest version
Get-WindowsUpdate -Online -Install -AcceptAll

# Check proxy settings
netsh winhttp show proxy
```

#### 5. "Permission denied errors"
**Symptoms**: File access errors, configuration save failures
**Solutions**:
```cmd
:: Run as Administrator (one-time setup)
Right-click "Polaris Node Manager.exe" → "Run as administrator"

:: Check folder permissions
icacls "%LOCALAPPDATA%\Polaris Node Manager" /t /q
```

### Event Log Monitoring
Monitor Windows Event Log for Polaris-related events:

```powershell
# View Polaris events in Event Viewer
Get-WinEvent -FilterHashtable @{LogName='Application'; ProviderName='Polaris Node Manager'}

# Monitor security-related events
Get-WinEvent -FilterHashtable @{LogName='Security'; ID=4624,4625} | Where-Object {$_.Message -like "*Polaris*"}
```

### Network Diagnostics
```powershell
# Test connectivity to Polaris servers
Test-NetConnection polariscloud.ai -Port 443 -InformationLevel Detailed

# Check DNS resolution
Resolve-DnsName polariscloud.ai

# Test TLS connectivity
$webRequest = [System.Net.WebRequest]::Create("https://polariscloud.ai")
$webRequest.GetResponse()
```

## Performance Optimization

### Windows-Specific Optimizations
- **Hardware Acceleration**: Utilizes Windows CNG for cryptographic operations
- **Memory Management**: Windows heap optimization for reduced memory usage
- **I/O Performance**: Optimized file I/O using Windows overlapped I/O
- **Network Stack**: Uses Windows TCP/IP stack optimizations

### Resource Usage
- **Memory**: ~75MB base usage (+15MB for security features)
- **CPU**: <1% idle usage, 2-5% during active operations
- **Disk**: Minimal I/O, primarily for logging and configuration
- **Network**: Efficient connection pooling, typically <1MB/hour background traffic

## Security Best Practices

### Windows Environment Security
1. **Keep Windows Updated**: Ensure automatic Windows Updates are enabled
2. **Use Standard User Account**: Run application with standard user privileges when possible
3. **Enable Windows Defender**: Keep real-time protection enabled
4. **Regular Scans**: Perform regular system scans with Windows Defender
5. **Firewall Configuration**: Keep Windows Firewall enabled with default settings

### Application Security
1. **Verify Downloads**: Always verify file checksums before installation
2. **Official Sources**: Only download from official GitHub releases
3. **Report Issues**: Report security concerns to security@polariscloud.ai
4. **Regular Updates**: Keep application updated to latest version
5. **Secure Credentials**: Never share your UID or credentials with others

## Enterprise Deployment

### Group Policy Configuration
For enterprise deployments, configure via Group Policy:

```xml
<!-- Group Policy template for Polaris Node Manager -->
<policy>
  <computerConfiguration>
    <administrativeTemplates>
      <application name="Polaris Node Manager">
        <setting name="AutoUpdate" value="Enabled" />
        <setting name="CertificateValidation" value="Strict" />
        <setting name="TLSMinVersion" value="1.3" />
      </application>
    </administrativeTemplates>
  </computerConfiguration>
</policy>
```

### System Center Configuration Manager (SCCM)
Deploy via SCCM using provided MSI package (available separately).

### Microsoft Intune
Configure application deployment through Microsoft Intune for modern device management.

## Support Information

### Windows-Specific Support Channels
- **Windows Issues**: windows-support@polariscloud.ai
- **Enterprise Support**: enterprise@polariscloud.ai
- **Security Issues**: security@polariscloud.ai

### System Information for Support
When contacting support, include:

```powershell
# Generate system information report
$systemInfo = @{
    "Windows Version" = (Get-WmiObject Win32_OperatingSystem).Caption
    "Build Number" = (Get-WmiObject Win32_OperatingSystem).BuildNumber
    "TLS Version" = [Net.ServicePointManager]::SecurityProtocol
    "Installed Updates" = (Get-HotFix | Sort-Object InstalledOn -Descending | Select-Object -First 5)
    "Certificate Store" = (Get-ChildItem Cert:\LocalMachine\Root | Where-Object {$_.Subject -like "*polariscloud*"}).Count
}
$systemInfo | ConvertTo-Json
```

## Version Information

- **Version**: 2.0.4
- **Windows Build**: 2.0.4-windows-x64
- **Security Level**: Enhanced
- **Support Until**: January 2025
- **Minimum Windows Version**: Windows 10 Build 20348
- **Recommended Windows Version**: Windows 11 22H2 or later

---

**Security Notice**: This version contains critical security updates. Upgrading from previous versions is strongly recommended. Always download from official sources and verify file integrity before installation.