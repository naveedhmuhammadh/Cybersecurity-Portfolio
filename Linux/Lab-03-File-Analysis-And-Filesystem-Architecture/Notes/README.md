# Lab 03 Notes

## File Analysis Commands

### cat

Displays file contents.

Example:

```bash
cat investigation.log
```

---

### head

Displays the first lines of a file.

Example:

```bash
head -2 investigation.log
```

---

### tail

Displays the last lines of a file.

Example:

```bash
tail -2 investigation.log
```

---

### wc

Counts lines, words, and characters.

Example:

```bash
wc investigation.log
wc -l investigation.log
```

---

### file

Identifies the real file type by analyzing its contents.

Example:

```bash
file investigation.log
```

Important security concept:

File extensions cannot always be trusted.

---

### stat

Displays file metadata.

Example:

```bash
stat investigation.log
```

Shows:

* Size
* Permissions
* Owner
* Group
* Access time
* Modification time

---

### less

Used to view large files interactively.

Example:

```bash
less /etc/services
```
Uses an absolute path to open the file with the "less" file viewer, since it is outside the current working directory. The leading slash (/) directs the system to look from the root directory, allowing to view the file from any location in the filesystem.

Navigation:

* Space = Next page
* b = Previous page
* / = Search the keyword on the search prompt using " / "
* q = Quit

---

## Linux Filesystem Hierarchy

### /

Root of the Linux filesystem.

All directories originate from this location.

---

### /home

Stores user files and personal data.

Example:

```text
/home/hex
```

---

### /etc

Stores system configuration files.

Examples:

```text
/etc/hosts
/etc/passwd
/etc/ssh
```

---

### /var/log

Stores system and application logs.

Important for:

* SOC investigations
* Incident response
* Troubleshooting

---

### /usr

Contains applications, binaries, libraries, and documentation.

---

### /boot

Contains kernel and boot-related files required for startup.

---

### /dev

Contains device files.

Linux treats devices as files.

Examples:

```text
/dev/null
/dev/tty
```

---

### /proc

Virtual filesystem generated dynamically by the Linux kernel.

Provides information about:

* CPU
* Memory
* Processes
* Kernel state

---

## Key Concept

Linux Philosophy:

```text
Everything Is A File
```

This includes:

* Regular files
* Directories
* Devices
* Process information
* Kernel information

