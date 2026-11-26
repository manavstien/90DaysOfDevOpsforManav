# Linux Commands Cheatsheet

## 1. Process Management

| Command | Usage |
|---|---|
| `ps aux` | List running processes. |
| `ps -p PID -o pid,ppid,comm` | Inspect a specific process. |
| `top` | Monitor processes and resource usage interactively. |
| `pgrep -a java` | Find Java processes and their command lines. |
| `kill PID` | Request graceful termination of a process (SIGTERM). |
| `kill -9 PID` | Forcefully terminate a process (SIGKILL). |
| `jobs` | List jobs running in the current shell. |
| `bg` / `fg` | Resume a suspended job in the background or foreground. |
| `nice` / `renice` | Start or change a process's scheduling priority. |

## 2. Filesystem Management

| Command | Usage |
|---|---|
| `pwd` | Display the current working directory. |
| `ls -lah` | List files, including hidden files, with readable sizes. |
| `cd /path` | Change the current directory. |
| `mkdir -p dir/subdir` | Create directories, including missing parent directories. |
| `touch file.txt` | Create an empty file or update its timestamp. |
| `cp source destination` | Copy a file. |
| `mv source destination` | Move or rename a file. |
| `rm file.txt` | Delete a file. |
| `cat file.txt` | Display file contents. |
| `less file.txt` | Browse a file interactively. |
| `head -n 10 file.txt` | Display the first 10 lines. |
| `tail -f app.log` | Follow new log entries in real time. |
| `find . -name "*.log"` | Find files by name. |
| `grep -in "error" app.log` | Search for text, ignoring case and showing line numbers. |
| `chmod 755 script.sh` | Change file permissions. |
| `chown user:group file.txt` | Change file ownership. |
| `df -h` | Display filesystem capacity and available space. |
| `du -sh directory` | Display the total size of a directory. |

## 3. Networking and Troubleshooting

| Command | Usage |
|---|---|
| `ping -c 4 google.com` | Test network reachability using ICMP. |
| `ip addr` | Display network interfaces and IP addresses. |
| `ip route` | Display the routing table and default gateway. |
| `dig google.com` | Query DNS records. |
| `dig +short google.com` | Display concise DNS results. |
| `nslookup google.com` | Perform a DNS lookup. |
| `curl -I https://example.com` | Retrieve HTTP response headers. |
| `curl -v https://example.com` | Inspect connection and HTTP details. |
| `ss -tuln` | List listening TCP and UDP sockets. |
| `ss -ltnp` | List listening TCP ports and associated processes. |
| `traceroute google.com` | Trace the network path to a destination. |

## 4. Logs and System Inspection

| Command | Usage |
|---|---|
| `journalctl -n 50` | Display the latest 50 system log entries. |
| `journalctl -f` | Follow system logs in real time. |
| `journalctl -u service-name` | Display logs for a systemd service. |
| `journalctl -xe` | Inspect recent logs with additional context. |
| `free -h` | Display memory and swap usage. |
| `uptime` | Display system uptime and load averages. |
| `vmstat 1 5` | Display five system performance reports, one second apart. |
| `lsof -i :8080` | Identify processes using port 8080. |

---

**Day 03 objective:** Practise process management, filesystem operations, networking troubleshooting, and system inspection using Linux commands.
