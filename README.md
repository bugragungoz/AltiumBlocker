# Altium Designer Blocker

PowerShell script for selective network blocking of Altium Designer while preserving Component Search and Login functionality.

## Overview

Advanced network blocking tool that selectively restricts Altium Designer's internet connectivity. Unlike traditional blockers, this script preserves Component Search, Manufacturer Part Search, and authentication capabilities while blocking telemetry and license validation.

## Features

- Selective blocking: Component Search preserved
- Windows Firewall rule creation (inbound/outbound)
- Hosts file modification with selective domain blocking
- Service detection and reporting
- Automated backup and rollback capability
- Multiple operation modes (Block, Unblock, Dry Run, Rollback)
- Comprehensive logging and execution reports
- Multi-version support (AD20, AD21, AD22, AD23, AD24, AD25, etc.)

## Special Capabilities

### Preserved Functions
- Component Search functionality
- Manufacturer Part Search
- Online component databases (Octopart, PartQuest, AltiumLive)
- User login and authentication
- Library downloads and access
- API endpoints for component data

### Blocked Functions
- License validation servers
- Telemetry and analytics
- Automatic software updates
- Usage tracking
- Marketing communications

## Requirements

- Windows 10/11
- PowerShell 5.1 or later
- Administrator privileges

## Usage

```powershell
# Run as Administrator
.\AltiumDesignerBlocker.ps1
```

Select operation mode from interactive menu:
1. Block Mode - Apply selective blocking rules
2. Dry Run Mode - Preview changes without applying
3. Unblock Mode - Remove all blocking rules
4. Rollback Mode - Restore from backup
5. Exit
6. Disclaimer & Help

## Technical Details

### Blocking Methodology

1. **Selective Firewall Rules**: Blocks only non-essential components
2. **Selective DNS Blocking**: Only telemetry and license domains blocked
3. **Service Detection**: Identifies and reports Altium-related Windows services
4. **Smart Filtering**: Preserves Component Search and authentication modules

### File Locations Scanned

- `C:\Program Files\Altium\AD*\`
- `C:\Program Files (x86)\Altium\AD*\`
- `C:\ProgramData\Altium\`
- `%LOCALAPPDATA%\Altium\`
- `%APPDATA%\Altium\`
- Custom installation directories (user-specified)

### Allowed Components (Not Blocked)

Components containing these keywords remain unblocked:
- ComponentSearch, Octopart, PartQuest, AltiumLive
- Library, LibraryLoader, VaultQuery, Manufacturer
- Login, Auth, Authentication, Session
- Database, WebService, API, REST
- X2.exe, DXP.exe, Altium Designer.exe

### Blocked Domains (Selective List)

- license.altium.com
- licensing.altium.com
- activate.altium.com
- telemetry.altium.com
- analytics.altium.com
- update.altium.com

Note: Component database and login domains are NOT blocked.

### Log Files

All operations generate logs in `AltiumBlocker_Logs/` directory:
- Execution logs: `AltiumBlocker_YYYYMMDD_HHMMSS.log`
- Backup files: `AltiumBlocker_Backups/FirewallRules_*.xml`
- Reports: `AltiumBlocker_Report_*.txt`

## Legal Disclaimer

This tool is provided for legal use only. Users are solely responsible for:
- Compliance with software licenses
- Compliance with local laws and regulations
- Any consequences arising from use of this script

The author accepts no responsibility for misuse, damage, or legal consequences.

## Uninstallation

Remove all blocking rules:

```powershell
.\AltiumDesignerBlocker.ps1
# Select option 3: UNBLOCK MODE
```

## Technical Specifications

- Script Version: 1.0.0
- Rule Prefix: AltiumBlocker
- Session ID Format: YYYYMMDD_HHMMSS
- Backup Format: XML
- Supported Versions: AD20, AD21, AD22, AD23, AD24, AD25, and future releases
- Special Mode: Selective Blocking with Component Search Preservation

## Author

Bugra

## Development

Claude 4.5 Sonnet & Gemini 2.5 Pro AI

## License

See LICENSE file for details.

