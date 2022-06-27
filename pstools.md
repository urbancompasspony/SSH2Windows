# Remote

## Commands to use psexec from pstools!

If needed, put these parameters on commands, but normally they are not needed:

`\\HOSTNAME@DOMAIN -u USER -p PASSWORD`

To run applications that needs UI/GUI remotely and starting them on the Windows system, 
do like these examples:

psexec -d -i 1 APPLICATION.exe

To run batch scripts remotely, and without showing the cmd window, 
do like these examples:

psexec -d -i 1 C:/PSExecScripts/Quiet.exe C:/PSExecScripts/BATCH_FILE.bat

If you need to run an application like something.jar (java), use my example from this repository: 
https://github.com/urbancompasspony/SSH2Windows/blob/main/C:/PSExecScripts/Example.bat

You can run these commands automatically from Linux with:

ssh USER@IP_ADDRESS "psexec -d -i 1 C:/PSExecScripts/Quiet.exe C:/PSExecScripts/BATCH_FILE.bat"

Write something to a file...

echo test > C:/Temp/test.txt

...and open that file, on the desktop remotely, to someone using Windows see what was writted!

psexec -d -i 1 notepad "C:/Temp/test.txt"

Take a note about parameter "-i 1".
If another digit, will not work.
