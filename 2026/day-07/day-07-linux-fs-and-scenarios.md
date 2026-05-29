## Linux File Syystem Hierarchy

#### Core Directories:

##### / (root)
- The starting point of everything on a Linux system, where all files and directories are physically or logically located.

> `   ls -l  ` ----->> / output: bin, boot

- I would use this directory to navigate to any system resource from the absolute start of the hierarchy.

##### /etc
- Contains system-wide configuration files and shell scripts used to initialize system settings.
> `  ls -l /etc  ` ----->> output: hosts, passwd
- I would use this when I need to modify system configurations like networking or user permissions.

##### /var/log
- Stores variable data files, specifically system and application logs that grow over time.
> `  ls -l /var/log  ` ---->> output: syslog, auth.log
- I would use this when troubleshooting system errors or monitoring application behavior.

#### Additional Directories:

##### /bin
- Contains essential command binaries that are required for the system to boot and run in single-user mode.
> `  ls -l /bin  ` ---->> output: bash, ls
- I would use this when executing fundamental system commands like navigating or managing files.

##### /opt
- Reserved for the installation of add-on application software packages from third-party vendors.
> `  ls -l /opt  ` ---->> output: google, containerd
- I would use this when installing standalone software that doesn't follow the standard file hierarchy.



  ## Scienario-Based Practice
**Scenario 1: Service Not Starting** 
```
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```

**Hint:**
- First check: Is the service running or failed?
- Then check: What do the logs say?
- Finally check: Is it enabled to start on boot?

`Troubleshooting Problem`
```
  
systemctl status myapp

#Why: To check the current state of the service and see if it is active, inactive, or failed.

journalctl -u myapp -n 50

#Why: To examine the last 50 lines of logs specific to the service for error messages or crash reports.

systemctl is-enabled myapp

#Why: To verify if the service is configured to start automatically upon system boot.

systemctl restart myapp

#Why: To attempt to clear any temporary glitches or hung states by performing a fresh start of the service.

```

---

**Scenario 2: High CPU Usage** 
```
Your manager reports that the application server is slow.
You SSH into the server. What commands would you run to identify
which process is using high CPU?
```

**Hint:**
- Use a command that shows **live** CPU usage
- Look for processes sorted by CPU percentage
- Note the PID (Process ID) of the top process

---

`Troubleshooting Problem`
```
top
#Why: This command provides a real-time, live view of the system's resource usage, allowing you to
      #see which processes are currently consuming the most CPU power.

ps aux --sort=-%cpu | head -10
#Why: This command generates a static snapshot of all processes, sorts them by CPU usage in descending
    #order, and displays the top 10, making it easy to pinpoint the specific PID of the offending process.
```

---
**Scenario 3: Finding Service Logs** 
```
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```

**Hint:**
- systemd services → logs are in journald
- Command pattern: `journalctl -u <service-name>`
- Use -n flag to limit number of lines
- Use -f flag to follow logs in real-time (like tail -f)

---
`Troubleshooting Problem`
```
journalctl -u docker

# Why: Since the service is managed by systemd, this command retrieves all logs specifically associated with
       the docker unit from the centralized journal.

Step 2: journalctl -u docker -n 50

# Why: This command restricts the output to the last 50 entries, allowing you to quickly focus on the most
#      recent events and potential errors without scrolling through historical data.

journalctl -u docker -f

# Why: This command follows the log in real-time, similar to 'tail -f', which is essential for observing
#      how the service behaves as you trigger actions or attempt to reproduce an issue.

```
---

**Scenario 4: File Permissions Issue** 
```
A script at /home/user/backup.sh is not executing.
When you run it: ./backup.sh
You get: "Permission denied"

What commands would you use to fix this?
```

**Hint:**
- First: Check what permissions the file has
- Understand: Files need 'x' (execute) permission to run
- Fix: Add execute permission with chmod

---
`Troubleshooting Problem`
```
ls -l /home/user/backup.sh

# Why: To check current file permissions and verify if the 'x' execute bit is missing for the user.

chmod +x /home/user/backup.sh

# Why: To grant execute permissions to the script, allowing it to be run as a program.

./home/user/backup.sh

# Why: To attempt running the script again and verify that the 'Permission denied' error is resolved.
```

# What I have learned in Day 07

Today I explored the Linux File System Hierarchy and practiced troubleshooting common system scenarios. My learning focused on:

1. Linux File System Hierarchy: Understanding the purpose of standard directories like /etc for configurations, /var for logs, and /bin for essential binaries.

2. Scenario-Based Troubleshooting:
- Service Management:
  - Learned how to diagnose service failures using systemctl and check detailed logs with journalctl to identify root causes.
- Performance Monitoring:
   - Practiced using top and ps commands to identify processes causing high CPU usage and resource bottlenecks.
- File Permissions:
   - Resolved "Permission denied" errors by identifying missing execute bits with ls -l and applying correct permissions using chmod.

These skills are fundamental for DevOps engineers to maintain system stability, automate deployments reliably, and respond quickly to infrastructure incidents.
