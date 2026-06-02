# Lab 01 Notes

## Terminal

The terminal is a command-line interface (CLI) that allows users to interact directly with the Linux operating system by executing commands.

---

## pwd

### Meaning

Print Working Directory

### Purpose

Displays the current location within the filesystem.

### Example

pwd

### Example Output

/home/kali

### Lab Environment Output

/home/hex

---

## ls

### Meaning

List

### Purpose

Displays files and directories located in the current directory.

### Example

ls

---

## ls -la

### Meaning

List All

### Purpose

Displays detailed information about files and directories, including hidden files.

### Breakdown

* l = Long listing format
* a = All files including hidden files

### Example

ls -la

---

## cd

### Meaning

Change Directory

### Purpose

Moves the user between directories.

### Examples

cd Documents

cd /home/kali

cd ~

cd ..

### Lab Environment Example

cd /home/hex

---

## Relative Path

A relative path begins from the current working directory.

### Example

If the current location is:

/home/kali

Then:

cd Documents

moves to:

/home/kali/Documents

### Lab Environment Equivalent

/home/hex/Documents

---

## Absolute Path

An absolute path begins from the root directory (`/`) and specifies the complete location.

### Example

cd /home/kali/Documents

### Lab Environment Equivalent

cd /home/hex/Documents

---

## Home Directory

The symbol `~` represents the current user's home directory.

### Default Kali Linux Example

For user:

kali

The home directory would be:

/home/kali

### Lab Environment Example

For user:

hex

The home directory is:

/home/hex

Therefore:

~

equals

/home/hex

---

## Prompt Structure

A typical Linux terminal prompt contains:

username@hostname

### Default Kali Linux

kali@kali

### Lab Environment

hex@0day

---

## Important Linux Directories

### /

Root directory of the Linux filesystem.

### /home

Contains user home directories.

### /etc

Contains system configuration files.

### /var

Contains variable system data.

### /var/log

Contains system log files.

### /usr

Contains applications, binaries, libraries, and utilities.

---

## Key Concepts Learned

### Filesystem Hierarchy

Linux organizes files and directories in a hierarchical structure beginning at the root directory (`/`).

### Relative vs Absolute Paths

Relative paths depend on the current location.

Absolute paths always begin at the root directory and point directly to the target location.

### Navigation

Efficient navigation is one of the most important Linux skills and serves as the foundation for administration, troubleshooting, log analysis, scripting, and cybersecurity operations.

---

## Personal Notes

The most important concept learned during this lab was understanding how Linux organizes files and directories in a hierarchical structure and how relative and absolute paths affect navigation throughout the filesystem.
