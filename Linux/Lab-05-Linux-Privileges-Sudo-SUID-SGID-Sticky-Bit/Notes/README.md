# Lab 05 Notes

## Linux Privilege Architecture

Linux uses a permission-based security model.

Every action performed on a Linux system is evaluated against:

```text
User
Group
Permissions
Ownership
```

The operating system determines whether access should be granted or denied based on these factors.

---

# Root Account

The root account is the most privileged account in Linux.

Important fact:

```text
UID 0 = Root
```

Linux ultimately trusts UID 0 rather than the account name itself.

Root can:

- Read any file
- Modify any file
- Delete any file
- Create users
- Manage services
- Configure the operating system

---

# whoami

Displays the currently logged-in user.

Example:

```bash
whoami
```

Example Output:

```text
hex
```

Note:

`hex` is the username configured on this system.

Other systems may display:

```text
kali
john
alice
admin
```

---

# id

Displays detailed user identity information.

Example:

```bash
id
```

Example Output:

```text
uid=1000(hex) gid=1000(hex)
```

Explanation:

- uid = User ID
- gid = Group ID

Linux internally identifies users using numerical IDs.

---

# sudo

Meaning:

```text
Super User Do
```

Allows authorized users to execute commands with elevated privileges.

Example:

```bash
sudo whoami
```

Output:

```text
root
```

This demonstrates temporary privilege elevation.

---

# Principle of Least Privilege

Users should only receive the minimum permissions necessary to perform their tasks.

Benefits:

- Reduces risk
- Limits accidental damage
- Reduces attack surface
- Improves security

---

# which

Locates the executable file associated with a command.

Example:

```bash
which sudo
```

Example Output:

```text
/usr/bin/sudo
```

Linux executes this binary whenever the sudo command is used.

---

# SUID (Set User ID)

SUID allows a program to run with the permissions of the file owner.

Normal execution:

```text
User → Program → User Privileges
```

SUID execution:

```text
User → Program → File Owner Privileges
```

---

## Identifying SUID

Example:

```bash
ls -l /usr/bin/sudo
```

Output:

```text
-rwsr-xr-x
```

The letter:

```text
s
```

indicates SUID.

---

## Why sudo Uses SUID

A normal user cannot perform administrative actions.

sudo requires root privileges to execute privileged operations.

SUID allows sudo to operate with root privileges while being executed by a regular user.

---

## Why passwd Uses SUID

Password information is stored in protected system files.

Users must be able to change their passwords without receiving unrestricted administrative access.

SUID allows passwd to update protected password data securely.

---

# Discovering SUID Files

Example:

```bash
find /usr/bin -perm -4000 2>/dev/null
```

Purpose:

Locate files configured with SUID permissions.

Security professionals often review SUID files during security assessments and privilege escalation testing.

---

# SGID (Set Group ID)

SGID allows newly created files within a directory to inherit the directory's group ownership.

This improves collaboration in shared environments.

Common use cases:

- Security teams
- Development teams
- Shared projects
- Administrative groups

---

## Applying SGID

Example:

```bash
chmod g+s TeamShare
```

Verification:

```bash
ls -ld TeamShare
```

Example Output:

```text
drwxr-sr-x
```

The letter:

```text
s
```

appears in the group execute position.

---

# Sticky Bit

Sticky Bit is primarily used on shared writable directories.

It prevents users from deleting files belonging to other users.

---

## Example

Directory:

```text
/tmp
```

Verification:

```bash
ls -ld /tmp
```

Example Output:

```text
drwxrwxrwt
```

The letter:

```text
t
```

indicates Sticky Bit.

---

# Why Sticky Bit Is Important

Without Sticky Bit:

```text
User A can delete User B's files.
```

With Sticky Bit:

```text
Users can only delete their own files.
```

This protects shared directories from accidental or malicious file deletion.

---

# Error Redirection

Example:

```bash
find /usr/bin -perm -4000 2>/dev/null
```

Meaning:

```text
2 = Standard Error (stderr)
```

Redirect:

```text
stderr → /dev/null
```

---

# /dev/null

Special Linux device that discards any data written to it.

Often referred to as:

```text
Linux Black Hole
```

Anything redirected to /dev/null is permanently discarded.

---

# Security Perspective

Understanding Linux privileges is essential because many attacks involve:

- Privilege Escalation
- Misconfigured Permissions
- SUID Abuse
- Unauthorized Administrative Access

Security professionals routinely investigate these areas during:

- Hardening Activities
- Security Audits
- Incident Response
- Penetration Testing

---

# Key Takeaway

Linux security is built upon:

```text
Users
↓
Groups
↓
Permissions
↓
Ownership
↓
Privilege Management
```

Understanding these concepts is essential before moving into processes, services, logging, networking, and advanced security topics.
