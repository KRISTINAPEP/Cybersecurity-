# Linux Command Practice

This file logs my hands-on practice with basic Linux commands as I build fluency for SOC analyst work.

## Commands Practiced

### `pwd`
Prints the current working directory. Helps you know where you are in the file system.

### `ls`
Lists files and folders in the current directory.

### `mkdir practice_folder`
Creates a new folder called `practice_folder`.

### `cd practice_folder`
Moves into the folder you just created.

### `touch notes.txt`
Creates an empty file named `notes.txt`.

### `echo "My first Linux note!" > notes.txt`
Writes text into the file.

### `cat notes.txt`
Displays the contents of the file.

---

More commands coming soon as I continue practicing.

### `whoami`
Displays the current logged-in user. Useful for verifying identity during investigations.

### `chmod 644 notes.txt`
Changes file permissions. This sets read/write for owner, and read-only for others.

### `ps aux`
Lists all running processes. Helps identify suspicious activity or resource hogs.

### `kill <PID>`
Terminates a process by its ID. Used in incident response to stop malicious processes.

### `history`
Shows your recent commands. Great for auditing or retracing steps.

### `clear`
Clears the terminal screen. Just for tidiness.
