# ansibleWindowsServer
Automate Windows server patching


# allow ping useful for TS
 New-NetFirewallRule -Name "Allow ICMPv4-In" -DisplayName "Allow ICMPv4" -Enabled True -Protocol ICMPv4 -Direction Inbound -Action Allow

# allow win-RM Http, use 5986 for Https
 New-NetFirewallRule -Name "Allow WinRM" -DisplayName "Allow WinRM" -Enabled True -Protocol TCP -Direction Inbound -Action Allow -LocalPort 5985
