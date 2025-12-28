#WSL Basic Linux Commands

## Installing WSL (Windows Subsystem for Linux)

Run the following command in **PowerShell as Administrator**:

wsl --install

Ubuntu will open automatically
Set a Linux username and password
Once this is done, the Linux environment is successfully set up on Windows.

#Linux basic commands

#whoami
To check current user.

##mkdir directory_name
To make a directory.

##pwd
shows current directory path where the user is working.(Print Working Directory)

##cd directory_name
Moves into the specified directory(change directory).

##cd ..
To move one directory back.

##cd ~
current working directory to the user's home directory.

##mv existing file/directory name changing file/directory name
It changes file names.(move)

##touch file_name
creates a file.

##vim file_name
To create and write file at a time
To exit: i for insert mode to write and you must press i or any operation key.To exit press esc and shift + ; and type wq and enter. 

##nano filename
To write something to a file.
To exit nano: ctrl+x > press y if you want to save or press n for no > enter. 

##cat file_name
Shows content in that file.

##echo "write something here"
Prints write something here.

##rm filename
To delete the file (be careful once deleted no archiving).

##clear 
Clears the terminal.

##ls
Lists all files and folders in the current directory.

##ls -la 
Lists all files, including hidden files, along with detailed information such as permissions, owner, and file size.

##history
To see all executed commands.

##To exit Linux 
Open new poweshell tab and type(wsl --shutdown) enter.
