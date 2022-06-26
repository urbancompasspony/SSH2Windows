# Windows

Sequence of configurations and parameters to control, start and stop processes remotelly over SSH on Windows 10, 11 or even Server, from Linux.

# Dependencies

1) Install and configure OpenSSH Server on your Linux.
2) Install and configure OpenSSH Server on Windows.
Use this: https://github.com/PowerShell/Win32-OpenSSH/releases/latest
Install it: OpenSSH-Win64-vx.x.x.x.msi

Run on PowerShell as Administrator:
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
