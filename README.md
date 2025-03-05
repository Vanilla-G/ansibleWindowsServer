# ansibleWindowsServer
# Automate Windows server patching

# Run the following command to allow ICMP Echo Request (ping) through the firewall:
# This will create a rule allowing inbound ICMPv4 traffic, which is used for ping.
New-NetFirewallRule -Name "Allow ICMPv4-In" -DisplayName "Allow ICMPv4" -Enabled True -Protocol ICMPv4 -Direction Inbound -Action Allow

# Allow WinRM traffic (port 5985) through the Windows Defender Firewall: 
# You need to enable the Windows Remote Management (WinRM) port (5985 for HTTP or 5986 for HTTPS).
# PowerShell but open as admin
New-NetFirewallRule -Name "Allow WinRM" -DisplayName "Allow WinRM" -Enabled True -Protocol TCP -Direction Inbound -Action Allow -LocalPort 5985


# If you're using WinRM over HTTPS (port 5986), run this instead:
New-NetFirewallRule -Name "Allow WinRM HTTPS" -DisplayName "Allow WinRM HTTPS" -Enabled True -Protocol TCP -Direction Inbound -Action Allow -LocalPort 5986


# Verify the Rules: You can verify that the rules are in place by running:
Get-NetFirewallRule | Where-Object {$_.Name -match "ICMPv4|WinRM"}
