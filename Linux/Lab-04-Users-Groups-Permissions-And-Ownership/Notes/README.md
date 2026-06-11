# Lab 04 Notes

## User Identification Commands

### whoami

Displays the username of the currently logged-in user.

Example:

```bash
whoami
```

Example Output:

```text
hex
```

Explanation:

- `hex` is the username configured on this Kali Linux virtual machine.
- On another Linux system, the output may be different.

Examples:

```text
kali
john
alice
admin
```

Purpose:

Used to verify which user account is currently active.

---

### id

Displays detailed user identity information.

Example:

```bash
id
```

Example Output:

```text
uid=1000(hex) gid=1000(hex) groups=1000(hex),27(sudo)
```

Explanation:

- `uid` = User ID
- `gid` = Primary Group ID
- `groups` = Groups the user belongs to
- `1000` = UID assigned to this user
- `hex` = Username configured on this system

Note:

Usernames and UID values vary between Linux installations.

Purpose:

Linux internally identifies users using numeric IDs rather than usernames.

---

### groups

Displays the groups that the current user belongs to.

Example:

```bash
groups
```

Example Output:

```text
hex sudo audio video cdrom
```

Explanation:

- `hex` = Primary user group on this system
- `sudo` = Administrative privileges
- `audio` = Audio device access
- `video` = Video device access
- `cdrom` = Optical drive access

Note:

Group memberships vary depending on:

- Linux distribution
- Installed software
- System configuration
- User privileges

Purpose:

Used to verify permissions and access rights.

---

# Linux Permission Model

Linux controls access using three permission categories:

```text
Owner
Group
Others
```

Every file and directory is assigned permissions for each category.

---

## Owner

The user account that owns a file or directory.

Example:

```text
hex
```

Explanation:

- `hex` is the owner username on this system.
- On another Linux machine the owner name may be different.

Examples:

```text
kali
john
alice
admin
```

The owner usually has the highest level of control over the file.

---

## Group

A collection of users that share permissions.

Example:

```text
sudo
developers
soc
security
```

Explanation:

Users who belong to the assigned group inherit the group's permissions.

Benefits:

- Easier administration
- Centralized access management
- Better scalability

---

## Others

Any user who is neither:

- The owner
- A member of the assigned group

These users receive the permissions assigned under the "Others" category.

---

# Permission Types

Linux permissions are represented by:

```text
r = Read
w = Write
x = Execute
```

---

## Read (r)

Numeric Value:

```text
4
```

Allows:

- Viewing file contents
- Reading data

Example:

```bash
cat file.txt
```

---

## Write (w)

Numeric Value:

```text
2
```

Allows:

- Modifying file contents
- Editing files

Example:

```bash
echo "New Data" >> file.txt
```

---

## Execute (x)

Numeric Value:

```text
1
```

Allows:

- Running programs
- Executing scripts

Example:

```bash
./script.sh
```

---

# Permission Calculations

Linux combines permission values using addition.

Example:

## rwx

```text
4 + 2 + 1 = 7
```

Result:

```text
rwx
```

Meaning:

Full access.

---

## rw-

```text
4 + 2 = 6
```

Result:

```text
rw-
```

Meaning:

Read and Write.

---

## r--

```text
4
```

Result:

```text
r--
```

Meaning:

Read only.

---

# Common Permission Values

### 644

```text
rw-r--r--
```

Owner:

```text
Read + Write
```

Group:

```text
Read
```

Others:

```text
Read
```

Commonly used for:

- Configuration files
- Documentation
- Text files

---

### 700

```text
rwx------
```

Owner:

```text
Read + Write + Execute
```

Group:

```text
No Access
```

Others:

```text
No Access
```

Commonly used for:

- Private files
- Sensitive directories

---

### 755

```text
rwxr-xr-x
```

Owner:

```text
Read + Write + Execute
```

Group:

```text
Read + Execute
```

Others:

```text
Read + Execute
```

Commonly used for:

- Directories
- Scripts
- Executable files

---

### 777

```text
rwxrwxrwx
```

Everyone receives:

```text
Read
Write
Execute
```

Security Risk:

Avoid using 777 unless absolutely necessary.

Potential Risks:

- Unauthorized modification
- Malware placement
- Privilege abuse

---

# chmod

Changes file or directory permissions.

Syntax:

```bash
chmod PERMISSIONS FILE
```

Examples:

```bash
chmod 700 security.txt
chmod 644 security.txt
chmod 755 security.txt
```

Purpose:

Modify access permissions.

---

# chown

Changes ownership of a file or directory.

Syntax:

```bash
sudo chown USER FILE
```

Example:

```bash
sudo chown user1 report.txt
```

Explanation:

- `user1` is an example username.
- On another system this could be any valid user account.

Purpose:

Transfer ownership to another user.

---

# Root Account

Linux contains a special administrative account:

```text
root
```

Important Fact:

```text
UID 0 = Root
```

Explanation:

The Linux kernel grants unrestricted privileges to any process running with UID 0.

Root can:

- Read any file
- Modify any file
- Delete any file
- Manage users
- Control services
- Administer the entire operating system

---

# /etc/passwd

Stores user account information.

Example Entry:

```text
root:x:0:0:root:/root:/bin/bash
```

Important Fields:

- Username
- UID
- GID
- Home Directory
- Login Shell

Note:

The exact contents of `/etc/passwd` differ between systems because user accounts differ.

---

# Security Importance

Permissions are one of the most important security controls in Linux.

They determine:

- Who can read data
- Who can modify data
- Who can execute programs

Incorrect permissions may lead to:

- Unauthorized access
- Data tampering
- Information disclosure
- Privilege escalation

---

# Key Concept

Linux Security Foundation:

```text
User
↓
Group
↓
Permissions
↓
Ownership
```

Everything in Linux administration, SOC operations, incident response, and penetration testing builds upon these concepts.
