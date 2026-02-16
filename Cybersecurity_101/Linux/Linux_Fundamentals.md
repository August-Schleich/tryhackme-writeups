## Linux Fundamentals (Parts 1-3)

**Difficulty:** Easy | **Type:** Learning Path

### Overview
A three-part series introducing essential Linux command-line skills for cybersecurity professionals. These rooms build foundational knowledge required for penetration testing, system administration, and security operations.

### What You'll Learn

**Part 1:** Basic Linux commands, file system navigation, and searching for files
- Commands: `ls`, `cd`, `cat`, `pwd`, `find`, `grep`
- Understanding the Linux directory structure
- Basic file operations

**Part 2:** File permissions, operators, and system information
- User permissions and `chmod`
- Shell operators (`>`, `>>`, `&&`, `&`)
- System commands and package management

**Part 3:** Text editors, utilities, and process management
- Using `vim` and `nano`
- Downloading files with `wget`
- Managing processes and automation with `cron`

### Key Takeaways
These rooms establish the Linux CLI proficiency needed for virtually every other TryHackMe room. Master these commands—they're the foundation of everything in cybersecurity operations.

## Linux Fundamentals Part 1 - Solution Breakdown

### Task 3: Running Your First Commands
**Challenge:** Find the flag in the home directory

**Solution:**
```bash
ls                    # List files in current directory
cat flag.txt          # Read the flag file
```
**Flag:** `THM{...}`

**Key Learning:** Basic navigation and file reading

---

### Task 4: Searching for Files
**Challenge:** Locate a specific file on the system

**Solution:**
```bash
find / -name filename.txt 2>/dev/null    # Search entire system, hide errors
# OR
find /home -type f -name "*.txt"         # Search home directory for text files
```
**Flag:** `THM{...}`

**Key Learning:** Using `find` with pattern matching and error redirection

---

## Linux Fundamentals Part 2 - Solution Breakdown

### Task 3: File Permissions
**Challenge:** Change file permissions and execute a script

**Solution:**
```bash
ls -la script.sh              # Check current permissions
chmod +x script.sh            # Make executable
./script.sh                   # Run the script
# OR
chmod 755 script.sh           # Numeric permissions
```
**Key Learning:** Understanding rwx permissions and octal notation

---

### Task 5: Shell Operators
**Challenge:** Use operators to chain commands

**Solution:**
```bash
command1 && command2          # Run command2 only if command1 succeeds
cat file1.txt > output.txt    # Redirect output to file
cat file2.txt >> output.txt   # Append to file
cat output.txt | grep "flag"  # Pipe to grep to find flag
```

---

## Linux Fundamentals Part 3 - Solution Breakdown

### Task 2: Text Editors
**Challenge:** Edit a file using vim/nano

**Solution (Vim):**
```bash
vim file.txt
# Press 'i' for insert mode
# Make changes
# Press 'ESC' then ':wq' to save and quit
```

**Solution (Nano):**
```bash
nano file.txt
# Make changes
# CTRL+X, then Y to save, Enter to confirm
```

---

### Task 4: Downloading Files
**Challenge:** Download a file from a web server

**Solution:**
```bash
wget http://example.com/file.txt           # Download file
curl http://example.com/file.txt -o file.txt    # Alternative with curl
python3 -m http.server 8000                # Start local web server (if needed)
```

---

### Task 5: Process Management
**Challenge:** Find and manage running processes

**Solution:**
```bash
ps aux                        # List all processes
ps aux | grep apache          # Find specific process
top                           # Interactive process viewer
kill [PID]                    # Terminate process
kill -9 [PID]                 # Force kill
```

---

### Task 6: Automation with Cron
**Challenge:** Schedule a task to run automatically

**Solution:**
```bash
crontab -e                    # Edit cron jobs
# Add line: */5 * * * * /path/to/script.sh   # Runs every 5 minutes
crontab -l                    # List current cron jobs
```

**Cron Syntax:** `minute hour day month weekday command`

---

## General Methodology

1. **Read the question carefully** - Understand what's being asked
2. **Check your current location** - Use `pwd` to know where you are
3. **List available files** - Use `ls -la` to see what's available
4. **Use man pages** - `man [command]` when unsure about syntax
5. **Redirect errors** - Add `2>/dev/null` to hide permission errors when searching
6. **Take notes** - Document commands that work for future reference

## Common Pitfalls

- Forgetting to use `sudo` for privileged operations
- Not redirecting stderr when using `find` 
- Incorrect file paths (relative vs absolute)
- Forgetting to make scripts executable with `chmod +x`