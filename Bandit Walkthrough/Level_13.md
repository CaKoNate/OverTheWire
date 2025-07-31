## Bandit Level 13 → Level 14

### 🎯 Goal
The password for the next level is located in `/etc/bandit_pass/bandit14`, but you are not given the password directly. Instead, you're provided with an SSH private key to log into `bandit14`.

---

### 🔧 Solution Steps

1. Create a temporary directory and copy the key file  
> 💡 Note: We use a temporary directory because the home directory is read-only and cannot be used for file operations.

```bash
mkdir /tmp/yourname
cp sshkey.private /tmp/yourname/
chmod 600 /tmp/yourname/sshkey.private
```
2. Use the private key to SSH into the next level:
> 💡 Note: You must specify port 2220; otherwise, it will use the default port (22), which will result in a connection error.

 ```bash
    ssh -i sshkey.private -p 2220 bandit14@localhost
```

3. Once logged in, retrieve the password using:

```bash

cat /etc/bandit_pass/bandit14

```


## ⚠️ Notes

You cannot change file permissions on sshkey.private in the home folder, so copy it to /tmp first.

chmod 600 is necessary; otherwise, SSH will refuse to use the key.

localhost means you're connecting to the same machine.