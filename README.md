# Ansible Windows Server Patching

## Overview
This guide provides steps to configure Windows Firewall rules for ICMP (ping) and WinRM to facilitate Ansible automation on Windows Servers.

## Firewall Configuration

### 1. Allow ICMP (Ping) Traffic
To allow ICMP Echo Request (ping) through the firewall, run the following PowerShell command:

```powershell
New-NetFirewallRule -Name "Allow ICMPv4-In" -DisplayName "Allow ICMPv4" -Enabled True -Protocol ICMPv4 -Direction Inbound -Action Allow
```

### 2. Allow WinRM Traffic
WinRM (Windows Remote Management) is required for Ansible to communicate with Windows servers. Run the appropriate command based on your WinRM configuration.

#### Allow WinRM over HTTP (Port 5985)
```powershell
New-NetFirewallRule -Name "Allow WinRM" -DisplayName "Allow WinRM" -Enabled True -Protocol TCP -Direction Inbound -Action Allow -LocalPort 5985
```

#### Allow WinRM over HTTPS (Port 5986)
```powershell
New-NetFirewallRule -Name "Allow WinRM HTTPS" -DisplayName "Allow WinRM HTTPS" -Enabled True -Protocol TCP -Direction Inbound -Action Allow -LocalPort 5986
```

### 3. Verify Firewall Rules
To confirm the firewall rules are in place, run the following command:

```powershell
Get-NetFirewallRule | Where-Object {$_.Name -match "ICMPv4|WinRM"}
```

## Notes
- Run PowerShell as Administrator when executing these commands.
- Ensure WinRM is properly configured for Ansible to connect successfully.

## Additional Resources
- [Ansible Documentation for Windows](https://docs.ansible.com/ansible/latest/user_guide/windows.html)
- [Microsoft Docs - WinRM](https://docs.microsoft.com/en-us/windows/win32/winrm/portal)

