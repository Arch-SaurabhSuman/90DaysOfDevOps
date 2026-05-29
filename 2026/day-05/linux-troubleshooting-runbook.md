## Linux Troubleshooting Runbook

#### Target Service: `ssh`
```
systemctl status ssh
```
*Observation:* The SSH service is active and running, allowing remote secure connections to the system.

#### Environment Basics
```
uname -a
```
Observation: Displays the Linux kernel version and hardware architecture to ensure compatibility with system tools.
```
lsb_release -a
```
Observation: Confirms the OS distribution , which helps in identifying the correct package manager and configuration paths.

#### Filesystem Sanity
```
mkdir /tmp/runbook-demo && cp /etc/hosts /tmp/runbook-demo/hosts-copy
```
Observation: Successfully created a directory and copied a file, confirming that the filesystem is writable and permissions are intact.
```
ls -l /tmp/runbook-demo
```
Observation: Verified the existence and permissions of the copied file to ensure data integrity during temporary operations.

#### CPU and Memory Snapshot
 ```
top -bn1 | head -n 15
```
Observation: Provides a snapshot of CPU usage and top processes.
```
free -h
```
Observation: Displays available physical and swap memory. 

#### Disk and I/O Snapshot
```
df -h
```
Observation: Shows disk space usage across partitions; the root partition has plenty of free space for logs and data.
```
iostat
```
Observation: Monitors CPU statistics and input/output statistics for devices; I/O wait times are low, then Idle

#### Network Snapshot
```
 ss -tulpn
```
Observation: Lists all listening ports and their associated processes; confirmed port 22 is open for SSH.
```
ping -c 4 google.com
```
Observation: Verified external network connectivity and latency

#### Logs Reviewed
```
journalctl -u ssh -n 50
```
Observation: Scanned the last 50 lines of SSH logs
```
tail -n 50 /var/log/syslog
```
Observation: Checked general system logs for hardware or kernel errors



##### If things worsen
- Restart the service using `systemctl restart ssh ` to clear any potential hangs.
- Increase log verbosity in `/etc/ssh/sshd_config` to gather more detailed debug information.
- Use` strace -p $(pidof sshd)` to monitor system calls and identify where the process might be blocking.
