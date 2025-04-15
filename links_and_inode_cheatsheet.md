
# Soft Link, Hard Link, and Inode in Linux

## What is a Soft Link?

A **symbolic link** (symlink or soft link) is a special type of file that points to a source file or directory.  
It acts like a shortcut in Windows — it contains the path to the original file rather than the file contents.

### Syntax

```bash
ln -s <sourcefile> <destfile>
ln -s <full_path_to_sourcefile> <full_path_to_destfile>
```

---

## What is a Hard Link?

A **hard link** is a mirror copy of the original file.  
Deleting the original file does not affect the hard link, as it still holds the data (same inode).

### Syntax

```bash
ln <sourcefile> <destfile>
unlink <file_or_directory>
```

---

## Difference Between Soft Link and Hard Link

### Soft Link (Symbolic Link)

1. Acts like a shortcut in Windows.
2. Changes in the link or original reflect in both.
3. Can be created across different file systems.
4. Can link both files and directories.
5. Has a different inode number and file permissions than the original.
6. If the original file is deleted, the soft link becomes a broken or hanging link.

### Hard Link

1. Acts as a mirror copy of the original file.
2. Works like a soft link.
3. Must be created within the same file system.
4. Can only link files (not directories).
5. Shares the same inode number and file permissions.
6. Remains valid even if the original file is deleted.

---

## What is the Inode Number?

An **inode** is a data structure in Linux used to store metadata about a file.

Each file/directory has a unique inode number, also known as an index number.

### Attributes Stored in Inode:

- File size
- Owner information
- Date and time (creation, modification)
- Permissions and access control
- Physical location on disk
- File type
- Number of links
- Additional metadata

### Commands to View Inode Information

```bash
ls -li       # List files with inode numbers
stat <file>  # Detailed inode and file metadata
```
