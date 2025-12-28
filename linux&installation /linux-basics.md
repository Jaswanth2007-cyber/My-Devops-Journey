#WSL Basic Linux Commands

## Installing WSL (Windows Subsystem for Linux)

Run the following command in **PowerShell as Administrator**:

wsl --install

Ubuntu will open automatically
Set a Linux username and password
Once this is done, the Linux environment is successfully set up on Windows.

# WSL and Basic Linux Commands

## Installing WSL (Windows Subsystem for Linux)

Run the following command in **PowerShell as Administrator**:

wsl --install
Ubuntu will open automatically.

Set a Linux username and password.

Once this is done, the Linux environment is successfully set up on Windows.

## Linux Basic Commands
### System Info
whoami :  To check current user.

pwd :  Shows current directory path where the user is working (Print Working Directory).

clear :  Clears the terminal screen.

history :  To see all previously executed commands.

### File & Directory Management
ls :  Lists all files and folders in the current directory.

ls -la :  Lists all files, including hidden files, with detailed information (permissions, owner, size).

mkdir [directory_name] :  To make a new directory.

touch [file_name] :  Creates a new empty file.

mv [existing_name] [new_name] :  Moves or renames a file/directory.

rm [filename] :  To delete a file (Caution: No undo/archiving).

cat [file_name] :  Shows the content inside a file.

echo "text" :  Prints the specified text to the terminal.

### Navigation
cd [directory_name]: Moves into the specified directory.

cd  . . :  To move one directory back.

cd  ~ :  Moves to the user's home directory.

### Text Editors
Nano
To open :  nano filename

To exit :  Press Ctrl + X, then press Y to save (or N to discard), then hit Enter.

Vim
To open :  vim filename

To write :  Press i to enter Insert mode.

To save & exit :  Press Esc, then type :wq and hit Enter.

### Exit Linux (Shutdown WSL)

Open a new PowerShell tab and type:

wsl  --shutdown -> hit enter.
