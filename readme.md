# Windows

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

5) Download a little application named QUIET. I put it on C:/PSExecScripts/

Download: https://www.joeware.net/freetools/tools/quiet/index.htm

# Remote

To run applications that needs UI/GUI remotely and starting them on the Windows system, do like these examples:

psexec \\HOSTNAME -u USER -p PASSWORD -d -i 1 C:/PSExecScripts/quiet.exe application.exe

To run batch scripts remotely, and without prompting the cmd window, do like these examples:

psexec \\HOSTNAME -u USER -p PASSWORD -d -i 1 C:/PSExecScripts/quiet.exe C:/PSExecScripts/batch_file.bat

If you need to run an application like something.jar (java), use my example from "SSH2Windows/C:/PSExecScripts" folder on this repository!
https://github.com/urbancompasspony/SSH2Windows/blob/main/C:/PSExecScripts/Example.bat
