#WSL Basic Linux Commands

## Installing WSL (Windows Subsystem for Linux)

Run the following command in **PowerShell as Administrator**:

```powershell

wsl --install

Ubuntu will open automatically
Set a Linux username and password
Once this is done, the Linux environment is successfully set up on Windows.

#Linux basic commands

#whoami
To check current user.

##pwd
shows current directory path where the user is working.(Print Working Directory)

##mkdir directory_name
To make a directory.

##ls
Lists all files and folders in the current directory.

##ls -la 
Lists all files, including hidden files, along with detailed information such as permissions, owner, and file size.

##cd directory_name
Moves into the specified directory(change directory).

##cd ..
To move one directory back.

##mv existing file/directory name changing file/directory name
It changes file names.(move)

##touch file_name
creates a file.

##vim file_name
To create and write file at a time 

##cat file_name
shows content in that file.

##rm filename
to delete the file (be careful once deleted no archiving).

##clear 
everything on screen clears.

##echo "write something here"
prints write something here.

##nano filename
To write something to a file.
To exit nano: ctrl+x > press y if you want to save or press n for no > enter.

##history
To see all executed commands.
