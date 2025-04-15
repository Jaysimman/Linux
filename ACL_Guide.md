
# Access Control List (ACL)

An **access ACL** is the access control list on a specific file or directory for specific users or group members.

---

## Verify Default ACL on a File/Folder

```bash
getfacl <file/foldername>
```

---

## Set ACL on a File for a Specific User

```bash
setfacl -m u:username:rwx <filename>
setfacl -m 'u:username:7' <filename>
```

---

## Set ACL on a File for a Specific Group

```bash
setfacl -m g:groupname:rwx <filename>
setfacl -m g:groupname:7 <filename>
```

---

## Remove ACL for a Specific User

```bash
setfacl -x u:username <file/folder>
```

---

## Remove ACL for a Specific Group

```bash
setfacl -x g:groupname <file/folder>
```

---

## Remove All ACLs from a File/Directory

```bash
setfacl -b <file/directory>      # Remove all ACLs
```

---

## Recursive ACL Commands

```bash
getfacl -R /secure
setfacl -R -m g:groupname:rwx <filename>
setfacl -x u:balaji:rwx
getfacl
setfacl -b
```
