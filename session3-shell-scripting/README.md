# Shell Scripting — System Information Script

## Objective

Create a Bash script to display system information, accept user input, create a directory and file, and save running process information using output redirection.

## 1. Shell Script (`system_info.sh`)

```bash
#!/bin/bash

# Take user input
read -p "Enter your name: " name

# Store system information in variables
current_date=$(date)
hostname=$(hostname)
username=$(whoami)
disk_usage=$(df -h)
running_processes=$(ps aux)

# Display system information
echo "===== SYSTEM INFORMATION ====="
echo "Hello, $name!"
echo "Date: $current_date"
echo "Hostname: $hostname"
echo "Username: $username"

echo ""
echo "===== DISK USAGE ====="
echo "$disk_usage"

echo ""
echo "===== RUNNING PROCESSES ====="
echo "$running_processes"

# Create directory and file
mkdir -p system_info
touch system_info/processes.txt

# Save running processes to the file
ps aux > system_info/processes.txt

echo ""
echo "Process information saved to system_info/processes.txt"
```

## 2. Execute the Script

```bash
chmod +x system_info.sh
./system_info.sh
```

## 3. Sample Output

```text
Enter your name: Naman

===== SYSTEM INFORMATION =====
Hello, Naman!
Date: Sat Oct 17 17:00:00 IST 2026
Hostname: example-host
Username: naman

===== DISK USAGE =====
Filesystem      Size  Used Avail Use% Mounted on
/dev/example    100G   40G   60G  40% /

===== RUNNING PROCESSES =====
USER       PID %CPU %MEM COMMAND
root         1  0.0  0.1 /sbin/init
naman     1234  0.1  0.5 bash

Process information saved to system_info/processes.txt
```

*Note: The output above is illustrative. Actual results depend on the system.*

## 4. Verify the Generated File

```bash
ls -l system_info/
cat system_info/processes.txt
```

## 5. GitHub Submission

```bash
git init
git add system_info.sh README.md
git commit -m "Add system information shell script"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
git push -u origin main
```

Replace the repository URL with your actual public GitHub repository URL.

