### Linux Architecture Core Components

**1. Kernel**
 - The core of the operating system that acts as a bridge between hardware and software. It manages CPU, memory,
devices, and filesystems. It runs in privileged kernel space.

**2. User Space**
 - The area where user applications, libraries, and shells run. It is isolated from the kernel for security and
 stability.

**3. systemd** 
 - In Linux, systemd is the system and service manager that acts as the first process (PID 1) to start during boot.
   the 'd' stands for daemon—a background process that manages system services without user intervention.
   Understanding systemd is essential for `managing how applications start, run, and log their activities
   on a Linux server`.

### Process Management

A process is an instance of a running program with a unique Process ID (PID). 
- Creation: Most processes start via fork() (creating a copy) and exec() (replacing the copy with a new program).
- States: Processes move through states like Running (R), Sleeping (S), Stopped (T), or Zombie (Z).
- Lifecycle: Managed by the kernel to ensure fair resource allocation using the scheduler.

### systemd and Why It Matters

systemd is the first process (PID 1) that starts after the kernel boots. It is the system and service manager
for modern Linux.

#### Key systemd Unit Types:
- .service: Manages background daemons (e.g., docker, nginx).
- .timer: Schedules tasks (replaces cron).
- .mount: Manages file system mounts.
- .target: Groups units (e.g., multi-user.target).

#### systemd Commands:
| # | COMMAND | DESCRIPTION |
|----|---|---|
| 1. | systemctl status <service>       | Check service health and logs.        |
| 2. | systemctl restart <service>      | Apply config changes or fix hangs.    |
| 3. | systemctl enable --now <service> | Enable at boot and start immediately. |
| 4. | journalctl -u <service> -f       | View live logs for debugging.         |
| 5. | systemctl list-units --failed    | Quickly identify system issues.       |


#### Daily use command
```
top
ps -aux
df -h
free -h
systemctl
journalctl -u <service/app>
```


#### Why this matters for DevOps:
 - Understanding these fundamentals is critical for troubleshooting server failures, optimizing application
performance, and automating infrastructure deployments securely. It is the foundation of managing production
environments.
