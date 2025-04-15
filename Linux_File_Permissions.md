
# Linux File Permissions

## Types of Permissions

1. Basic file/folder permissions  
2. Special file/folder permissions  
3. Access control list (ACL)

---

## Basic File/Folder Permissions

### To check the default permission of a file/folder

```bash
ls -l
ll
```

Example output:
```
-rw-r--r-- 1 root root 292 Dec  9 12:59 testfile1  
drwxr-xr-x 2 root root 54 Dec  8 16:10 secure
```

### Fields in `ls -l` command output

```
<file type> <file permission> <link count> <owner> <group> <file size> <last modify date/time> <file name>
```

| File Type | User | Group | Others |
|-----------|------|--------|--------|
| d         | rwx  | r-x    | r-x    |
| -         | rw-  | r--    | r--    |
| l         | rwx  | rwx    | rwx    |

---

## `ls` Command Options

```bash
ls -iadRrlt
```

| Option | Description |
|--------|-------------|
| i      | List inode number |
| a      | Show hidden files/folders |
| d      | Show directories only |
| R      | Recursive listing |
| l      | Long listing format |
| r      | Reverse order |
| t      | Sort by modification time |

---

## File Permissions

- **Read**: Permission to read the content  
- **Write**: Permission to modify content  
- **Execute**: Permission to run as script

## Directory/Folder Permissions

- **Read**: List contents (`ls`)  
- **Write**: Create/delete files/folders  
- **Execute**: Change into the directory

---

## Access Classes

- **User (u)** – File owner  
- **Group (g)** – Users in the file’s group  
- **Others (o)** – Everyone else

---

## Changing File/Directory Permissions

```bash
chmod [permission] <file/directory>
```

### Methods

1. **Octal/Numeric**  
2. **Symbolic (rwx)**

#### Numeric Values

- Read = 4  
- Write = 2  
- Execute = 1

Example:

| Symbolic | Numeric |
|----------|---------|
| rwx      | 7       |
| rw-      | 6       |
| r--      | 4       |

```bash
# Numeric Method
chmod 744 <file>
chmod 440 <file>
chmod 244 <file>

# Symbolic Method
chmod u=rwx,g=rw,o=r <file>
chmod u-x,g-rw,o+r <file>
chmod a=rwx testfile1
chmod a-wx testfile1
chmod a+wx testfile1
```

| Who | Meaning |
|-----|---------|
| u   | user |
| g   | group |
| o   | others |
| a   | all |

---

## Default Permissions

### Normal User

- Directory: 775  
- File: 664

### Root

- Directory: 755  
- File: 644

---

## `umask` – Default Permissions

`umask` controls the default permissions for new files and directories.

### Full permissions:
- File: 666  
- Directory: 777

**Default = Full - umask**

#### Root user umask = 022  
#### Normal user umask = 002

### Example Calculations

#### Root

```text
File:      666 - 022 = 644  
Directory: 777 - 022 = 755
```

#### Normal User

```text
File:      666 - 002 = 664  
Directory: 777 - 002 = 775
```

### Change `umask`:

- Per user: Add `umask 222` to `~/.bash_profile`  
- All users: Modify `/etc/profile`

---

## Change Ownership

```bash
# Change both user and group
chown user:group <file>
chown -R user:group <dir>

# Change only owner
chown user <file>

# Change only group
chown :group <file>
chgrp group <file>
```

---

## Key Commands Summary

| Command | Purpose |
|---------|---------|
| `chmod` | Change file permissions |
| `chown` | Change owner and group |
| `chgrp` | Change group only |

---

# Special Permissions

## Types

1. **Setuid (SUID)** – 4  
2. **Setgid (SGID)** – 2  
3. **Sticky Bit** – 1

| Permission Type | Symbol |
|-----------------|--------|
| SUID            | s (user exec) |
| SGID            | s (group exec) |
| Sticky Bit      | t (others exec) |

```bash
chmod u+s <file>
chmod g+s <file>
chmod o+t <file>

chmod 4755 <file>
chmod 2755 <file>
chmod 1755 <file>
```

---

## Setuid (SUID)

- Grants executing user the privileges of the file owner.
- Numeric value: 4

```bash
chmod 4755 <file>
chmod u+s <file>
chmod u-s <file>
```

**Examples:**

```bash
ls -l /usr/bin/su
ls -l /usr/bin/mount
ls -l /usr/bin/passwd
```

---

## Setgid (SGID)

- Similar to SUID but applies to the group.
- Numeric value: 2

**For files:** Changes effective group ID.  
**For directories:** New files inherit the directory's group.

```bash
chmod 2755 <file/dir>
chmod g+s <file/dir>
chmod g-s <file/dir>
```

---

## Sticky Bit

- Only the file owner or root can delete files in the directory.
- Used in public/shared directories like `/tmp`.
- Numeric value: 1

```bash
chmod 1755 <dir>
chmod o+t <dir>
chmod o-t <dir>
```

---
