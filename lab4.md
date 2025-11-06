# Lab 5 - File & Backup Automation Documentation

## Objective
The objective of this assignment was to *automate file management* by creating a shell script (backup.sh) that specifically handles .txt files in the current directory, backing them up to a backup/ directory with a timestamp.

---

## Task 1: The backup.sh Script

### Script Code
*Include your full, tested backup.sh script here. Use a code block for clean formatting.*

```bash
Your 'backup.sh' script content goes here.
Example structure:
!/bin/bash
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
for file in *.txt; do
if [ -f "$file" ]; then
mkdir -p backup
cp "$file" "backup/${file%.txt}_${TIMESTAMP}.txt"
fi
done
```

### How the Script Works

* *Goal:* The script is designed to automate the process of finding and backing up all .txt files in the directory where it is executed.
* *Step-by-Step Explanation:*
    1.  *Timestamp Generation:* The script first defines a variable (e.g., TIMESTAMP) to hold the current date and time. This ensures a unique, chronologically sortable identifier for each backup. *Example: $(date +"%Y%m%d_%H%M%S")*
    2.  *Directory Creation:* It ensures that the target backup directory (backup/) exists. *Command: mkdir -p backup*
    3.  *File Iteration:* It then loops through all files in the current directory matching the pattern *.txt.
    4.  *Copy Operation:* For each file found, the cp command is used to copy the file into the backup/ directory.
    5.  *Renaming:* While copying, the filename is modified to include the generated timestamp, following the format originalfilename_timestamp.txt. This is usually achieved using *parameter expansion* to strip the original .txt and then append the timestamp and the extension back.

---

## Task 2: Example Run

*Show the commands you ran to test the script and the resulting file structure. You can use the tree command output or a simple ls -R output if tree is not available.*

### Initial State
Commands executed to create test files:

```bash
Example commands
touch file1.txt file2.txt notes.txt
ls -l
```

### Execution
Command to run the script:

```bash
./backup.sh
```

### Final State (Verification)
Command to verify the backup:

```bash
ls -l backup/

```
#### Expected output showing files with timestamps:
#### file1_20251106_102317.txt
#### file2_20251106_102317.txt
#### notes_20251106_102317.txt

---

## Extra Questions

### 1. What is the difference between cp, mv, and rsync?

cp copies files or directories, keeping the original intact; mv moves or renames files/directories, removing them from the source; rsync smartly syncs files and directories (locally or over a network), copying only changed parts and supporting resume, progress, and advanced options.

### 2. How can you schedule scripts to run automatically?

Scripts can be scheduled to run automatically on Unix-like operating systems (Linux, macOS) using either **cron** or **anacron** (for systems that are not always running).

* **cron**
    * *Purpose:* The primary job scheduler used to execute commands or scripts at specified times or intervals.
    * *Mechanism:* Jobs are defined in a configuration file called a *crontab*. The syntax uses five fields to define the minute, hour, day of the month, month, and day of the week.
    * *Example:* To run the backup.sh script every day at 1:30 AM, you would add this line to your crontab:
        \\\`
        30 01 * * * /path/to/your/backup.sh
        \\\`
    * *Note:* cron is ideal for servers or machines that are always powered on.

* **anacron**
    * *Purpose:* Used on systems that may be powered down or suspended, such as laptops or desktop machines.
    * *Mechanism:* It checks if a job was missed while the system was off and runs it when the system is next powered on. It uses days as its time interval.

---