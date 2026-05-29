# Linux Command Cheat Sheet for DevOps

### Process Management
| Command | Usage |
| :--- | :--- |
| ps aux         | Displays all running processes on the system.                       |
| top            | Provides a real-time, interactive view of running processes.        |
| htop           | An interactive process viewer (improved version of top).            |
| kill <PID>     | Sends a signal to a process to terminate it.                        |
| killall <name> | Kills all processes by name.                                        |
| bg             | Resumes a suspended job in the background.                          |
| fg             | Brings a background job to the foreground.                          |
| nice           | Starts a process with a specific priority.                          |

### File System & Permissions
| Command | Usage |
| :--- | :--- |
| ls -la | Lists files with detailed information including hidden files.|
| chmod 755 "file" | Changes file permissions (read/write/execute). |
| chown "user:group" | Changes file owner and group. |
| df -h | Shows disk space usage in human-readable format. |
| du -sh * | Summarizes disk usage of files and directories in current path. |
| find /path -name "file" | Searches for files in a directory hierarchy. |
| tar -czvf archive.tar.gz | Creates a compressed tar archive. |

### Networking
| Command | Usage |
| :--- | :--- |
| ping <host' | Sends ICMP ECHO_REQUEST to network hosts. |
| ip addr show | Displays IP addresses and network interface properties. |
| netstat -tunlp | Shows active network connections and listening ports. |
| curl -I 'url' | Fetches the HTTP header of a URL. |
| dig 'domain' | Performs DNS lookups and queries DNS name servers. |

### Troubleshooting & System Logs
| Command | Usage |
| :--- | :--- |
| journalctl -xe | Shows system logs with explanations for recent failures. |
| tail -f /var/log/syslog | Outputs the last part of a log file in real-time. |
| dmesg | Prints kernel ring buffer (hardware/driver errors). |
| lsof -i :80 | Lists open files associated with a specific port. |
| uptime | Shows system running time and load average. |
