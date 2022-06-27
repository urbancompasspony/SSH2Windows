# SSH2Windows

Sequence of configurations and parameters to control, start and stop processes remotelly over SSH 
on Windows 10, 11 or even Server, from Linux.

## Dependencies

1) Install and configure OpenSSH Server on your Linux.
2) Install and configure OpenSSH Server on Windows.
Use this: https://github.com/PowerShell/Win32-OpenSSH/releases/latest
Install it: OpenSSH-Win64-vx.x.x.x.msi

Run on PowerShell as Administrator:

`Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0`

`Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0`

Set-Service -Name sshd -StartupType 'Automatic'

Start-Service sshd

3) Connect through SSH.
Run:

powershell

Then:

New-ItemProperty -Path "HKLM:\SOFTWARE\OpenSSH" -Name DefaultShell -Value "C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe" -PropertyType String -Force

So PowerShell will become the main shell over SSH!

4) Download PSTools.exe and add it to PATH. Put where you want.

Download: https://docs.microsoft.com/en-us/sysinternals/downloads/pstools

When first run, accept EULA:

psexec /accepteula

5) Download a little application named QUIET. I put it on C:/PSExecScripts/

Download: https://www.joeware.net/freetools/tools/quiet/index.htm

6) Another nice optional tool is NirCMD, alternative to PSTools:

Download: https://www.nirsoft.net/utils/nircmd.html

And thats it!
Take a look at the files "commands" and "remote" of this repository.

# Permissions & Errors

If error with permissions, use this command first to temporary elevate your PowerShell environment:

net use \\MACHINE-NAME\ipc$ /user:USER_ADMINISTRATOR PASSWORD

To make it permanently, run this as administrator account:

reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v LocalAccountTokenFilterPolicy /t REG_DWORD /d 1 /f

Also, you need to enable Network Discovery, with:

netsh advfirewall firewall set rule group="Network Discovery" new enable=Yes

If it not work, use GUI inside Explorer.exe to enable! Just allow like Private Networks config.

Reboot your machine and everything will works!
