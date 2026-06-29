# Lab 06 Notes - Linux Processes, Services & System Monitoring

## Purpose of This Lab

The purpose of this lab was to understand how Linux runs programs, manages processes, controls services, and monitors system resources.

Everything running in Linux is associated with one or more processes. Understanding processes is critical for Linux administration, cybersecurity, incident response, threat hunting, and troubleshooting.

---

# What is a Process?

A process is a running instance of a program.

Examples:

- Firefox running
- Terminal running
- SSH running
- NetworkManager running

A program stored on disk becomes a process when Linux executes it.

Example:

```bash
firefox
```

When executed, Linux loads Firefox into memory and creates a process.

---

# Process ID (PID)

Every process running on Linux receives a unique identifier called a Process ID (PID).

Example:

```text
PID = 2548
```

Linux uses the PID to:

- Track processes
- Manage processes
- Stop processes
- Monitor processes

Without PIDs Linux would not know which process to control.

---

# Parent Process ID (PPID)

Every process is started by another process.

Linux records this relationship using the Parent Process ID (PPID).

Example:

```text
bash
 └── sleep
```

In this example:

- bash = Parent Process
- sleep = Child Process

The PPID points to the PID of the parent process.

---

# Parent and Child Processes

Linux processes exist in a hierarchy.

Example:

```text
systemd
 └── gnome-terminal
      └── zsh
           └── sleep
```

Relationship:

- systemd starts terminal
- terminal starts shell
- shell starts sleep

This is known as a parent-child relationship.

Understanding these relationships is extremely important during:

- Threat Hunting
- Malware Analysis
- Incident Response

---

# The ps Command

The `ps` command displays information about running processes.

Basic usage:

```bash
ps
```

Displays:

- PID
- TTY
- TIME
- COMMAND

---

## ps -ef

```bash
ps -ef
```

Meaning:

- `-e` = Every process
- `-f` = Full details

Displays:

- User
- PID
- PPID
- Start Time
- Command

Commonly used by Linux administrators.

---

## ps aux

```bash
ps aux
```

Displays:

- User
- PID
- CPU Usage
- Memory Usage
- Command

This is one of the most frequently used Linux troubleshooting commands.

SOC analysts and incident responders use it regularly.

---

# The pstree Command

Displays processes in a tree structure.

Command:

```bash
pstree
```

Example:

```text
systemd
 └── zsh
      └── sleep
```

Useful for:

- Understanding process relationships
- Identifying suspicious child processes
- Malware investigations

---

# The top Command

Command:

```bash
top
```

Purpose:

Real-time system monitoring.

Displays:

- CPU Usage
- Memory Usage
- Running Processes
- Load Average
- Uptime

Updates continuously.

Press:

```text
q
```

to exit.

---

# The htop Command

Command:

```bash
htop
```

Purpose:

Interactive process monitoring.

Advantages over top:

- Easier to read
- Colorized output
- Search functionality
- Process management shortcuts

Commonly preferred by Linux administrators.

Exit:

```text
F10
```

or

```text
q
```

---

# Searching for Processes

Command:

```bash
ps aux | grep zsh
```

Explanation:

`|`

Pipe operator.

Sends output from one command into another.

`grep`

Filters text.

The command shows only lines containing:

```text
zsh
```

Useful for locating specific processes.

---

# Foreground Processes

A foreground process occupies the terminal.

Example:

```bash
top
```

While running:

- Terminal is busy
- User must interact with it

---

# Background Processes

A background process runs without occupying the terminal.

Example:

```bash
sleep 300 &
```

Meaning:

```text
&
```

Run in background.

You can continue using the terminal while the process runs.

---

# jobs Command

Displays background jobs.

Command:

```bash
jobs
```

Example:

```text
[1]+ Running sleep 300 &
```

Useful for monitoring shell jobs.

---

# kill Command

Used to terminate processes.

Example:

```bash
kill 2548
```

Linux sends a termination signal to the process.

If successful:

Process stops running.

---

# Why Killing Processes Matters

Administrators often terminate: 

- Frozen applications
- Excessive CPU consumers
- Malware
- Unauthorized software

This is a fundamental Linux administration skill.

---

# Linux Services

A service is a long-running background process.

Examples:

- ssh
- NetworkManager
- cron

Services typically start automatically during boot.

---

# systemd

Modern Linux distributions use:

```text
systemd
```

systemd is the service manager responsible for:

- Starting services
- Stopping services
- Restarting services
- Monitoring services

systemd is one of the first processes started during boot.

---

# systemctl Command

Used to manage services.

Check status:

```bash
systemctl status ssh
```

Check another service:

```bash
systemctl status NetworkManager
```

Displays:

- Running state
- Service description
- Logs
- Process information

---

# Active Services

Command:

```bash
systemctl list-units --type=service
```

Displays:

- Active services
- Loaded services
- Service state

Useful during:

- Audits
- Hardening
- Incident response

---

# Memory Monitoring

Command:

```bash
free -h
```

Meaning:

- free = Display memory usage
- -h = Human readable

Displays:

- Total RAM
- Used RAM
- Free RAM
- Available RAM

---

# CPU Information

Command:

```bash
lscpu
```

Displays:

- CPU Architecture
- CPU Model
- Core Count
- Thread Count
- Virtualization Features

Useful for understanding system hardware.

---

# System Uptime

Command:

```bash
uptime
```

Displays:

- System running time
- Logged-in users
- Load averages

Useful for monitoring server stability.

---

# Open Files and Processes

Command:

```bash
lsof
```

Meaning:

```text
List Open Files
```

Important Linux concept:

Everything is treated as a file.

Examples:

- Regular files
- Network connections
- Devices
- Pipes

lsof helps identify which processes are using resources.

---

# Cybersecurity Relevance

Understanding Linux processes and services is critical for security professionals.

Attackers frequently:

- Launch malicious processes
- Create persistence mechanisms
- Install unauthorized services
- Abuse system resources

Security teams use process analysis to:

- Detect malware
- Investigate incidents
- Identify suspicious activity
- Monitor system health

---

# Commands Learned

```bash
ps
ps -ef
ps aux
pstree
top
htop
grep
jobs
kill
systemctl status
systemctl list-units --type=service
free -h
lscpu
uptime
lsof
```

---

# Key Takeaways

- A process is a running program.
- Every process has a PID.
- Every process has a parent process (PPID).
- Linux processes exist in a hierarchy.
- ps is used to view processes.
- pstree visualizes process relationships.
- top and htop monitor system activity.
- Background jobs allow multitasking.
- kill terminates processes.
- Services are managed by systemd.
- systemctl is used to manage services.
- free displays memory usage.
- lscpu displays processor information.
- uptime displays system runtime.
- lsof displays open files and resources.

---

# Lab Outcome

This lab established a strong understanding of Linux process management, service administration, and system monitoring.

These concepts form the foundation for future topics including:

- Linux Networking
- Log Analysis
- Threat Hunting
- Incident Response
- Malware Analysis
- Security Monitoring
- Penetration Testing
