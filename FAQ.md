## My PSExec is giving error of Permission Denied!

Do some things:

You need to enable Network Discovery, with:

netsh advfirewall firewall set rule group="Network Discovery" new enable=Yes

If it not work, use GUI inside Explorer.exe to enable it! Just allow like Private Networks config.

Use this command to temporary elevate your PowerShell environment:

net use \\MACHINE-NAME\ipc$ /user:USER_ADMINISTRATOR PASSWORD

To make it to aways open as Elevated Shell, run this as administrator account:

reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\system /v LocalAccountTokenFilterPolicy /t REG_DWORD /d 1 /f

Reboot your machine and everything will works!

## Windows created over PSExec remotely are being displayed without texts and colors, but something blank/empty.

Add -s parameter to PSExec command, being something like this:

psexec -s -d -i 1 "application.exe"

-s will run as System User, don't know why this solves the problem
