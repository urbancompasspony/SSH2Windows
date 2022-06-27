# NirCMD

## Commands to use with NirCMD; PSTools required!

## Examples:

Open the door of J: CD-ROM drive:

psexec -d -i 1 nircmd.exe cdrom open j:

Close the door of Y: CD-ROM drive	

psexec -d -i 1 nircmd.exe cdrom close y:

Increase the system volume by 2000 units (out of 65535):

psexec -d -i 1 nircmd.exe changesysvolume 2000

Decrease the system volume by 5000 units (out of 65535):

psexec -d -i 1 nircmd.exe changesysvolume -5000

Set the volume to the highest value:

psexec -d -i 1 nircmd.exe setsysvolume 65535

Mute the system volume:

psexec -d -i 1 nircmd.exe mutesysvolume 1

Unmute the system volume:

psexec -d -i 1 nircmd.exe mutesysvolume 0

Create a shortcut on your desktop that switch the system volume between the mute and normal state:

psexec -d -i 1 nircmd.exe cmdshortcut "~$folder.desktop$" "Switch Volume" mutesysvolume 2

Turn off the monitor:

psexec -d -i 1 nircmd.exe monitor off

Start the default screen saver:

psexec -d -i 1 nircmd.exe screensaver

Put your computer in 'standby' mode:

psexec -d -i 1 nircmd.exe standby

log off the current user:

psexec -d -i 1 nircmd.exe exitwin logoff

Ask if you want to reboot, and if you answer 'Yes', reboot the computer:

psexec -d -i 1 nircmd.exe qboxcom "Do you want to reboot ?" "question" exitwin reboot

Turn off your computer:

psexec -d -i 1 nircmd.exe exitwin poweroff

Close all your Explorer windows (My Computer, folders, and so on):

psexec -d -i 1 nircmd.exe win close class "CabinetWClass"

Set the Windows Calculator as top-most window (above all other windows):

psexec -d -i 1 nircmd.exe win settopmost title "Calculator" 1

Set the Windows Calculator back to regular window (non top-most window):

psexec -d -i 1 nircmd.exe win settopmost title "Calculator" 0

Create a shortcut to Windows calculator under Start Menu->Programs->Calculators:

psexec -d -i 1 nircmd.exe shortcut "f:\winnt\system32\calc.exe" "~$folder.programs$\Calculators" "Windows Calculator"

Hide the desktop window:

psexec -d -i 1 nircmd.exe win hide class progman

Show the desktop window (After hiding it in previous example):

psexec -d -i 1 nircmd.exe win show class progman

Kill (terminate) all instance of Internet Explorer processes:

psexec -d -i 1 nircmd.exe killprocess iexplore.exe

Create a shortcut on your desktop that opens the door of K: CDROM drive when you run it:

psexec -d -i 1 nircmd.exe cmdshortcut "~$folder.desktop$" "Open CDROM" cdrom open k:

Create a shortcut to NirSoft Web site on your desktop:

psexec -d -i 1 nircmd.exe urlshortcut "http://www.nirsoft.net" "~$folder.desktop$" "NirSoft"

Set the display mode to 800x600x24bit colors:

psexec -d -i 1 nircmd.exe setdisplay 800 600 24

Copy all shortcuts on your desktop to another folder (f:\temp\desktop):

psexec -d -i 1 nircmd.exe execmd copy "~$folder.desktop$\*.lnk" f:\temp\desktop

Restart your IIS:

psexec -d -i 1 nircmd.exe service restart w3svc

Restart MySql:

psexec -d -i 1 nircmd.exe service restart MySql

Open the desired Registry key/value in RegEdit:

psexec -d -i 1 nircmd.exe regedit "HKLM\Software\Microsoft\Windows\CurrentVersion" "CommonFilesDir"

Open the Registry key that you copied to the clipboard in RegEdit:

psexec -d -i 1 nircmd regedit "~$clipboard$"

Disable the screen saver:

psexec -d -i 1 nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 0

Enable the screen saver:

psexec -d -i 1 nircmd.exe regsetval sz "HKCU\control panel\desktop" "ScreenSaveActive" 1

Empty the recycle bin in all drives:

psexec -d -i 1 nircmd.exe emptybin

Answer 'Yes' to a standard Windows message-box:

psexec -d -i 1 nircmd.exe dlg "" "" click yes

Wait 2 seconds, and then save the current screen to shot.png (Take carefull about privacy!)

psexec -d -i 1 nircmd.exe cmdwait 2000 savescreenshot "f:\temp\shot.png"

Save 10 screenshots in a loop, and wait 60 seconds between the screenshot save calls. The filenames of the screenshot will contain the time and date of the saved screenshot.	

psexec -d -i 1 nircmd.exe loop 10 60000 savescreenshot c:\temp\scr~$currdate.MM_dd_yyyy$-~$currtime.HH_mm_ss$.png

Wait until Firefox is closed, and then say "Firefox was closed"	

psexec -d -i 1 nircmd.exe waitprocess firefox.exe speak text "Firefox was closed"
