# Lab 05 - Linux Privileges, sudo, SUID, SGID & Sticky Bit

## Overview

This lab focuses on Linux privilege management and special permission mechanisms used throughout Linux systems.

The exercises demonstrate how Linux controls administrative access, how users temporarily obtain elevated privileges, and how special permission bits such as SUID, SGID, and Sticky Bit influence system behavior.

These concepts are fundamental for:

- Linux Administration
- System Hardening
- Security Operations Center (SOC)
- Incident Response
- Privilege Escalation Analysis
- Penetration Testing

---

## Objectives

By completing this lab, I learned:

- The role of the root account
- How sudo provides temporary privilege elevation
- The Principle of Least Privilege
- How Linux identifies users through UIDs
- How to locate system binaries
- How SUID works
- How SGID works
- How Sticky Bit works
- Why these mechanisms are important from a cybersecurity perspective

---

## Tools and Commands Used

### `whoami`

Displays the username of the currently logged-in user.

### `id`

Displays detailed user information including the User ID (UID), Group ID (GID), and group memberships.

### `grep`

Searches for specific text patterns within files.

### `sudo`

Allows an authorized user to execute commands with elevated privileges.

### `which`

Displays the absolute path of an executable file.

### `ls`

Lists files and directories.

Common options used in this lab:

- `-l` → Displays detailed information such as permissions, ownership, size, and timestamps.
- `-d` → Displays information about a directory itself rather than its contents.

### `find`

Searches the filesystem for files and directories matching specific criteria.

### `chmod`

Changes file and directory permissions, including special permissions such as SUID, SGID, and Sticky Bit.

### `mkdir`

Creates a new directory.

---

## Key Concepts Covered

### Root Account

Linux contains a special administrative account called root.

The root account has unrestricted access to the operating system and is identified by UID 0.

---

### sudo

The sudo command allows authorized users to execute commands with elevated privileges without logging in directly as root.

This supports secure administration while following the Principle of Least Privilege.

---

### SUID (Set User ID)

SUID allows a program to run with the permissions of the file owner rather than the user executing it.

Common examples include:

- sudo
- passwd

---

### SGID (Set Group ID)

SGID allows files created inside a directory to inherit the directory's group ownership.

This is commonly used for shared team environments.

---

### Sticky Bit

Sticky Bit prevents users from deleting files owned by other users inside shared writable directories.

A common example is:

```text
/tmp
```

---

## Screenshots

### Screenshot 1 — User Identification

![User Identification](Screenshots/screenshot1-user-identification.png)

#### Command Used

```bash
whoami
id
```

#### Purpose

Identify the currently logged-in user and display detailed user information.

#### Explanation

`whoami` displays the current username.

`id` displays the User ID (UID), Group ID (GID), and all groups the user belongs to.

This helps verify the identity and permissions of the current user.

---

### Screenshot 2 — Root Account Investigation

![Root Investigation](Screenshots/screenshot2-root-passwd-entry.png)

#### Command Used

```bash
grep root /etc/passwd
```

#### Purpose

Locate the root account entry inside the Linux user database.

#### Explanation

`grep` searches for text patterns.

The output confirms that the root account exists and uses UID 0, which is the highest privilege level in Linux.

---

### Screenshot 3 — sudo Rights

![sudo Rights](Screenshots/screenshot3-sudo-rights.png)

#### Command Used

```bash
sudo -l
```

#### Purpose

Display the sudo privileges assigned to the current user.

#### Explanation

The command shows which commands the user is allowed to execute using sudo.

This helps administrators verify privilege assignments.

---

### Screenshot 4 — sudo Privilege Escalation

![sudo whoami](Screenshots/screenshot4-sudo-whoami.png)

#### Command Used

```bash
sudo whoami
```

#### Purpose

Verify privilege elevation using sudo.

#### Explanation

Although logged in as a standard user, the command executes with elevated privileges and returns:

```text
root
```

This demonstrates temporary privilege escalation.

---

### Screenshot 5 — Locating System Binaries

![which Commands](Screenshots/screenshot5-which-commands.png)

#### Command Used

```bash
which sudo
which passwd
```

#### Purpose

Locate the absolute path of executable binaries.

#### Explanation

`which` displays the exact path of the executable Linux will run when the command is entered.

Example:

```text
/usr/bin/sudo
/usr/bin/passwd
```

---

### Screenshot 6 — SUID on sudo

![sudo SUID](Screenshots/screenshot6-sudo-suid.png)

#### Command Used

```bash
ls -l /usr/bin/sudo
```

#### Purpose

Inspect the permissions assigned to the sudo binary.

#### Explanation

The `-l` option displays detailed file information.

The letter `s` in the owner permission field indicates that the SUID bit is enabled.

This allows sudo to run with the permissions of its owner, which is root.

---

### Screenshot 7 — Discovering SUID Files

![SUID Discovery](Screenshots/screenshot7-suid-discovery.png)

#### Command Used

```bash
find /usr/bin -perm -4000 2>/dev/null
```

#### Purpose

Search for SUID-enabled files.

#### Explanation

`find` searches the filesystem.

`-perm -4000` searches specifically for SUID files.

`2>/dev/null` suppresses error messages by redirecting them to the Linux null device.

---

### Screenshot 8 — passwd SUID Analysis

![passwd SUID](Screenshots/screenshot8-passwd-suid.png)

#### Command Used

```bash
ls -l $(which passwd)
```

#### Purpose

Inspect the passwd binary and verify its permissions.

#### Explanation

`$(which passwd)` is command substitution.

Linux first executes:

```bash
which passwd
```

and then passes the result to:

```bash
ls -l
```

The output confirms that the passwd utility also uses SUID permissions.

---

### Screenshot 9 — Sticky Bit Investigation

![Sticky Bit](Screenshots/screenshot9-sticky-bit-tmp.png)

#### Command Used

```bash
ls -ld /tmp
```

#### Purpose

Inspect the permissions of the shared temporary directory.

#### Explanation

The `-d` option displays information about the directory itself.

The letter `t` at the end of the permissions indicates that the Sticky Bit is enabled.

This prevents users from deleting files owned by other users.

---

### Screenshot 10 — SGID Practical Demonstration

![SGID Practice](Screenshots/screenshot10-sgid-practice.png)

#### Command Used

```bash
mkdir TeamShare
chmod g+s TeamShare
ls -ld TeamShare
```

#### Purpose

Demonstrate how SGID works on directories.

#### Explanation

`mkdir` creates the directory.

`chmod g+s` enables the Set Group ID bit.

`ls -ld` verifies the permissions.

The letter `s` in the group permission field confirms that SGID has been successfully applied.

---

## Cybersecurity Relevance

Understanding Linux privilege management is critical for security professionals.

Attackers frequently attempt to exploit:

- Misconfigured permissions
- Excessive privileges
- Vulnerable SUID binaries
- Weak access controls

Defenders must understand:

- Access control
- User permissions
- Ownership
- Privilege escalation paths

to effectively secure Linux systems and investigate suspicious activity.

---

## Lab Outcome

This lab provided practical experience with Linux privilege management and introduced the permission mechanisms that form the foundation of Linux security architecture.

The concepts learned in this lab will be directly applicable in future topics including:

- Linux Hardening
- Incident Response
- Security Monitoring
- Privilege Escalation Analysis
- Penetration Testing
