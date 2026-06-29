# Lab 01 - Terminal Fundamentals

## Objective

The objective of this lab was to become familiar with the Linux terminal, basic navigation commands, filesystem hierarchy, and path concepts. These foundational skills are essential for Linux administration, cybersecurity operations, penetration testing, and security engineering.

---

## Lab Environment

* VMware Workstation Pro
* Kali Linux
* NAT Network Configuration
* Lenovo Laptop

### Lab Environment Note

This lab was performed on a customized Kali Linux virtual machine.

Many Linux tutorials and default Kali Linux installations use:

* Username: kali
* Hostname: kali

For this lab environment, the following custom values were configured:

* Username: hex
* Hostname: 0day

As a result, screenshots and command outputs may display:

* hex@0day
* /home/hex

instead of:

* kali@kali
* /home/kali

The Linux concepts and commands remain exactly the same.

---

## Commands Practiced

### pwd

Displays the current working directory.

### ls

Lists files and directories within the current directory.

### ls -la

Lists files and directories including hidden files and detailed information.

### cd

Changes the current working directory.

---

## Procedures Performed

1. Opened the Kali Linux terminal.
2. Identified the current working directory using the `pwd` command.
3. Listed directory contents using the `ls` command.
4. Displayed hidden files and detailed information using `ls -la`.
5. Navigated between directories using the `cd` command.
6. Explored important Linux filesystem locations.
7. Practiced relative and absolute path navigation.
8. Examined the Linux directory hierarchy.

---

## Key Findings

* Linux filesystems begin at the root directory (`/`).
* Every file and directory exists beneath the root directory.
* User home directories are typically located under `/home`.
* Configuration files are commonly stored in `/etc`.
* System logs are commonly stored in `/var/log`.
* Relative paths depend on the current working directory.
* Absolute paths always begin with the root directory (`/`).

---

## Important Directories Explored

| Directory | Purpose                          |
| --------- | -------------------------------- |
| /         | Root directory of the filesystem |
| /home     | User home directories            |
| /etc      | System configuration files       |
| /var      | Variable system data             |
| /var/log  | System log files                 |
| /usr      | User applications and utilities  |

---

## Screenshots

The Screenshots folder contains evidence of the completed activities, including:

* Current working directory identification
* Directory listing commands
* Filesystem hierarchy exploration
* Directory navigation exercises

---

## Lessons Learned

This lab established the foundation required for working within Linux environments. Understanding filesystem hierarchy, command syntax, relative paths, and absolute paths is critical for future activities involving system administration, networking, security monitoring, malware analysis, and penetration testing.

---

## Status

Completed
