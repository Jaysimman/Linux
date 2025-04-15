
# Users and Group Administration in Linux

## Definitions

- **User**: A person who utilizes the Operating System services.
- **Group**: A collection of users.

---

## Linux Users

1. **Super user or root user (0)**: User with all permissions, access, and privileges.
2. **Static system user (1-200)**: Automatically created by the OS (e.g., daemon).
3. **System user (201-999)**: Created by installed packages (e.g., HTTP, DNS).
4. **Normal user (1000-60000)**: Manually created, limited privileges.

---

## Important User/Group Administration Files

- `/etc/passwd`
- `/etc/group`
- `/etc/shadow`
- `/etc/gshadow`
- `/etc/login.defs`
- `/etc/default/useradd`

---

## User Management Commands

### Create a User
```bash
useradd <username>
```

### Set Password
```bash
passwd <username>
```

### Delete a User
```bash
userdel <username>
userdel -r <username>  # with home & mail directory
```

### View Users
```bash
cat /etc/passwd
```

### View User Info
```bash
id <username>
id -un <username>
id -gn <username>
```

### Remove Password
```bash
passwd -d <username>
```

### Modify User Defaults
```bash
vim /etc/default/useradd
```

### Login Details
```bash
w
who
whoami
```

---

## Group Management

### Create Group
```bash
groupadd <groupname>
```

### View Groups
```bash
cat /etc/group
```

### Add User to Group
```bash
gpasswd -a user group
usermod -a -G group user
```

### Remove User from Group
```bash
gpasswd -d user group
```

### Change Primary Group
```bash
usermod -g <groupname> <username>
```

### Delete Group
```bash
groupdel <groupname>
```

---

## Change Ownership

```bash
chown <username> <file/folder>
chgrp <groupname> <file/folder>
chown <username>:<groupname> <file/folder>
```

---

## Extended Useradd Example

```bash
useradd -u 2000 -g 3000 -c "test user" -d /home/test1 -s /bin/sh <username>
useradd -M
useradd -e "2021-12-25" <username>
```

---

## Usermod Options

### Rename User
```bash
usermod -l newname oldname
```

### Change UID
```bash
usermod -u 1076 username
```

### Change User Info
```bash
usermod -c "Test User" username
```

### Change Home Directory
```bash
usermod -d /new/home username
```

### Change Shell
```bash
usermod -s /bin/sh username
```

### Set Expiry Date
```bash
usermod -e "YYYY-MM-DD" username
```

### Lock/Unlock User
```bash
usermod -L username
usermod -U username
```

---

## Chage - Password Policies

### View Password Info
```bash
chage -l username
```

### Set Min/Max/Warn/Inactive Days
```bash
chage -m 5 username
chage -M 20 username
chage -W 5 username
chage -I 5 username
chage -m 5 -M 20 -W 3 -I 7 username
```

### Set Expiry Date
```bash
chage -E YYYY-MM-DD username
```

### Force Password Change at First Login
```bash
chage -d 0 username
```

---

## Groupmod

### Change GID
```bash
groupmod -g 1087 groupname
```

### Rename Group
```bash
groupmod -n newgroup oldgroup
```

---

## Password Lock/Unlock

```bash
passwd -l username  # lock
passwd -u username  # unlock
```
