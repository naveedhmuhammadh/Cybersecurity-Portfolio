# Lab 04 – Users, Groups, Permissions & Ownership

## Objective

This lab focused on understanding how Linux controls access to files and directories using users, groups, permissions, and ownership. These concepts form the foundation of Linux security and are critical for system administration, cybersecurity operations, incident response, and penetration testing.

---

## Topics Covered

- User identification
- User IDs (UID)
- Group IDs (GID)
- Linux groups
- File ownership
- File permissions
- Permission calculations
- chmod
- chown
- Root account fundamentals

---

## Commands Practiced

```bash
whoami
id
groups
ls -l
chmod
chown
stat
```

---

## Practical Activities

### 1. User Identification

Used:

```bash
whoami
id
groups
```

to identify the currently logged-in user and group memberships.

### 2. File Ownership Analysis

Created a file and inspected ownership information using:

```bash
ls -l
```

### 3. Linux Permission Analysis

Learned how Linux permissions are represented:

```text
r = Read
w = Write
x = Execute
```

and how permissions are assigned to:

```text
Owner
Group
Others
```

### 4. Numeric Permissions

Practiced:

```text
700
644
755
777
```

and learned how Linux converts permissions using:

```text
Read = 4
Write = 2
Execute = 1
```

### 5. Permission Modification

Used:

```bash
chmod
```

to modify file permissions and verify the changes.

### 6. Ownership Investigation

Learned the purpose of:

```bash
chown
```

and explored ownership structures.

### 7. Root Account Investigation

Investigated:

```text
/ etc/passwd
```

to understand the Linux root account and UID 0.

---

## Screenshots

### User Identification

![User Identification](Screenshots/screenshot1-user-identification.png)

### Lab Workspace

![Lab Workspace](Screenshots/screenshot2-lab-workspace.png)

### File Ownership

![File Ownership](Screenshots/screenshot3-file-ownership.png)

### Permission Analysis

![Permission Analysis](Screenshots/screenshot4-permission-analysis.png)

### chmod 700

![chmod700](Screenshots/screenshot5-chmod700.png)

### chmod 644

![chmod644](Screenshots/screenshot6-chmod644.png)

### chmod 755

![chmod755](Screenshots/screenshot7-chmod755.png)

### chmod 777

![chmod777](Screenshots/screenshot8-chmod777.png)

### passwd Investigation

![passwd Investigation](Screenshots/screenshot9-passwd-investigation.png)

### stat Investigation

![stat Investigation](Screenshots/screenshot10-stat-passwd.png)

---

## Key Learning Outcomes

- Learned how Linux identifies users using UID values.
- Understood the role of groups in access management.
- Learned how Linux evaluates file permissions.
- Practiced modifying permissions using chmod.
- Understood ownership concepts and their security relevance.
- Learned why UID 0 represents the root account.
- Explored how permissions contribute to Linux security.

---

## Key Concepts Learned

### User

A user account represents an identity on the Linux system.

Example:

```text
hex
```

Linux internally identifies users using a UID rather than a username.

### Group

Groups are collections of users used to simplify permission management.

Instead of assigning permissions to many users individually, permissions can be assigned to a group.

### Ownership

Every file and directory has:

- An Owner
- A Group

These determine who has access to the resource.

### Permissions

Linux permissions are divided into:

```text
Owner
Group
Others
```

Permission types:

```text
r = Read
w = Write
x = Execute
```

### Root Account

The most privileged account in Linux.

Important fact:

```text
UID 0 = Root
```

The Linux kernel grants unrestricted privileges to any process running with UID 0.

---

## Security Relevance

Permissions are one of the most important security mechanisms in Linux.

Incorrect permissions can lead to:

- Unauthorized access
- Data modification
- Privilege abuse
- Malware execution
- Information disclosure

Understanding users, groups, ownership, and permissions is essential for:

- Linux Administration
- Security Operations (SOC)
- Incident Response
- Threat Hunting
- Penetration Testing
- Security Engineering
