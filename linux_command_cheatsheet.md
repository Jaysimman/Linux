
# Linux Command Cheatsheet

## Command to Create Directory

```bash
mkdir [option] dir_name
mkdir dir1
```

### Create Multiple Directories

```bash
mkdir dir1 dir2
mkdir dir{1..10}
```

### Create Parent Directories

```bash
mkdir -p /opt/sport/test/dir1
```

---

## Command to Create File

```bash
touch file1
touch file1 file2 file3
touch file{1..10}
```

---

## Create File & Overwrite a File

```bash
cat > testfile1
# Type content
# Press ctrl+D to save and exit
```

### Append Data to a File

```bash
cat >> testfile1
# Type additional content
# Press ctrl+D to save and exit
```

---

## View File Content

```bash
cat <file_name>
```

---

## Remove File

```bash
rm file1
rm -f dir1
```

---

## Remove Directory

```bash
rmdir dir1
rm -r dir1
rm -rf dir1
```

---

## Change Directory

```bash
cd <dir_name>
cd <dir_name>/<dir2_name>/<dir3_name>
cd ../          # Move to parent directory
cd ../..        # Move two levels up
cd -            # Go to previous directory
cd              # Move to user home directory
cd ~            # Move to user home directory
```

---

## List Files and Directories

```bash
ls
ls -l
ls -ld
ls -la
ls -ltr
ls -iR
```

### ls Command Options

```bash
ls -iadRrlt
```

- `i` : List file's inode number  
- `a` : Show hidden files  
- `d` : List directories only  
- `R` : Recursive listing  
- `l` : Long format listing  
- `r` : Reverse order  
- `t` : Sort by timestamp  

---

## Print Working Directory

```bash
pwd
```

---

## Fundamental File Types in Linux

- `-` : Regular file  
- `d` : Directory  
- `l` : Link file  
- `s` : Socket file (kernel communication)  
- `p` : Pipe file  
- `c` : Character device (e.g., terminal)  
- `b` : Block device file  

---

## View File Examples

```bash
cat <filename>
cat /etc/ssh/sshd_config

cat /etc/ssh/sshd_config | head
cat /etc/ssh/sshd_config | head -20
head -n 20 /etc/ssh/sshd_config

cat /etc/ssh/sshd_config | tail -n 15
tail /etc/ssh/sshd_config

cat /etc/ssh/sshd_config | less
less /etc/ssh/sshd_config

cat /etc/ssh/sshd_config | more
more /etc/ssh/sshd_config
```

---

## grep

```bash
cat /etc/passwd | grep balaji
cat /etc/passwd | grep -i balaji       # Case-insensitive
cat /etc/passwd | grep -v balaji       # Inverse match
cat /etc/passwd | grep -A2 balaji      # 2 lines after match
cat /etc/passwd | grep -B2 balaji      # 2 lines before match
cat /etc/passwd | grep -E 'balaji|hari'
```

---

## Copy File to Another Directory

```bash
cp <source_file> <destination_file>
cp my_file.txt /tmp
cp /etc/my_file.txt /tmp
```

### Copy Multiple Files

```bash
cp my_file.txt my_file2.txt my_file3.txt /new_directory
```

### Copy Directories

```bash
cp -R <source_folder> <destination_folder>
cp -R /etc /etc_backup
```

### Copy Multiple Directories

```bash
cp -R /etc/* /home/* /backup_folder
```

---

## Move Files and Directories

### Move File

```bash
mv file1 /tmp/
```

### Move Directory

```bash
mv test-dir /tmp/
```

### Rename File

```bash
mv file1 file2
```

### Rename Directory

```bash
mv test-dir test-1
```

---

## Miscellaneous Commands

```bash
clear
echo 'This is a test file' > file1

uname
ifconfig
df -h

command1; command2; command3
whoami
who am i
w
```