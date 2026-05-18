# Linux Commands Cheat Sheet

## Process Management Commands

| Command | Usage |
|---------|--------|
| `ps` | Display currently running processes |
| `top` | Show real-time system processes |
| `htop` | Interactive process viewer |
| `kill PID` | Terminate a process using PID |
| `pkill process_name` | Kill process using process name |
| `jobs` | Show background jobs |
| `bg` | Run stopped job in background |
| `fg` | Bring background job to foreground |
| `nohup command &` | Run command after logout |
| `free -h` | Display system memory usage |

---

## File System Commands

| Command | Usage |
|---------|--------|
| `pwd` | Show current directory |
| `ls -la` | List files with detailed view |
| `cd directory_name` | Change directory |
| `mkdir folder_name` | Create new directory |
| `touch file.txt` | Create empty file |
| `cp source destination` | Copy files/directories |
| `mv old new` | Move or rename files |
| `rm file.txt` | Remove file |
| `rm -rf folder_name` | Remove directory recursively |
| `cat file.txt` | Display file content |
| `nano file.txt` | Edit file using nano editor |
| `find / -name filename` | Search files in system |
| `df -h` | Show disk space usage |
| `du -sh folder_name` | Show folder size |
| `chmod 755 file.sh` | Change file permissions |

---

## Networking Troubleshooting Commands

| Command | Usage |
|---------|--------|
| `ping google.com` | Check internet connectivity |
| `ip addr` | Show IP address information |
| `curl website.com` | Fetch website response |
| `dig google.com` | DNS lookup information |
| `netstat -tulnp` | Show active network connections |
| `ss -tulnp` | Display listening ports |
| `traceroute google.com` | Trace network route |
| `wget URL` | Download files from internet |

---

## System Information Commands

| Command | Usage |
|---------|--------|
| `uname -a` | Show system information |
| `whoami` | Display current user |
| `uptime` | Show system uptime |
| `history` | Show command history |
| `clear` | Clear terminal screen |

---

# Notes
- Use `man command_name` to read command manual pages.
- Use `sudo` before commands when admin privileges are required.
- Practice commands daily for better Linux command-line confidence.

#90DaysOfDevOps
