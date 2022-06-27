# F.A.Q.

## How it works?

Basicaly you will use just PSExec from PSTools.

Then, if you want to add some resources to PSExec, use NirCMD but with PSExec or will not work through SSH.

Finally, if you want to run .bat scripts and not show the black window, just use the Quiet.exe script!

## What can I do with these scripts and line codes?

Write some automatic codes to run from SSH and/or CRON jobs from Linux systems to administrate automatic jobs for Windows systems.
You can do this for Windows 10, 11 or Server 2019 and 2022.

Almost every script that opens up a GUI will open on Windows System, not Linux! This is not like Xorg over SSH, you will not grab the Window openned.

Is something more to run applications that need graphical interface remotelly without Anydesk, TeamViewer or etc.

## Examples of something?

You can simple run a service or even start some application and keep it openned; For Windows Server it is comfy to work on.

Or when on Windows 10 you can troll someone, spy someone since SSH plus PSTools and NirCMD are invisible to normal use (but they are running in processes list, remember that). You can adjust audio, take screenshots, etc.

With controll of Windows through SSH, your imagination is what will limit you.

## My PSExec is giving errors of Permission Denied!

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
