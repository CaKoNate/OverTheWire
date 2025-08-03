# 🏴 Bandit Level 16 → Level 17

---

## 🎯 Level Goal

> The credentials for the next level can be retrieved by submitting the password of the current level to a port on `localhost` in the range `31000–32000`.

You must:

- Identify which ports have an active server listening.
- Determine which servers **speak SSL/TLS** and which don't.
- Submit the password **only** to the correct server.
- Only **one** of these servers will return the correct credentials — others will just echo the input.

📌 *Note: If you encounter messages like `DONE`, `RENEGOTIATING`, or `KEYUPDATE`, check the “CONNECTED COMMANDS” section in the `man` page.*

---

## 🛠 Commands You May Need

```bash
ssh, telnet, nc, ncat, socat, openssl, s_client, nmap, netstat, ss
```

---

## 🧭 Step 1: Scan All Ports Using Nmap

We begin by scanning the entire port range from 31000 to 32000 on localhost:

```bash
nmap -sV localhost -p 31000-32000
```

### 🔍 Sample Output:

```text
Starting Nmap 7.40 ( https://nmap.org ) at 2021-06-12 16:17 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00026s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
31691/tcp open  echo
31790/tcp open  ssl/unknown
31960/tcp open  echo
```

### 📌 Interpretation:

- Ports with `echo`: These servers just return your input — no SSL/TLS.
- Ports with `ssl/echo`, `ssl/unknown`: These use SSL/TLS and are potential targets.

Focus only on SSL-enabled ports: **31518** and **31790**.

---

## 🧪 Step 2: Submit Password to SSL Port

Assume our current level password is:

```text
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
```

We test the SSL port with this command:

```bash
echo kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx | openssl s_client -connect localhost:31790 -quiet
```

> ⚠️ **Important:**  
> The `-quiet` flag is **required**. Without it, the output may include debug info and disrupt the actual password response.

This command returns a **private SSH key** instead of the usual password.

---

## 🔐 Step 3: Save SSH Key and Set Permissions

Now that we’ve obtained the private key, let’s use it to log in as `bandit17`.

### ✅ Create temporary directory and store the key:

```bash
cd /tmp
mkdir temp17 && cd temp17
nano sshkey
# Paste the key content from above, then save with Ctrl+O, Enter, Ctrl+X
```

Or automatically generate the file:

```bash
keydir=$(mktemp -d)
cd "$keydir"
nano sshkey  # paste the key here
```

### 🔒 Set the correct permissions:

```bash
chmod 600 sshkey
```

---

## 🔑 Step 4: SSH into Bandit17 Using the Private Key

```bash
ssh -i sshkey -p 2220 bandit17@bandit.labs.overthewire.org
```

> You may need to type `yes` if prompted to accept the server fingerprint.

---

## 📖 Step 5: Retrieve the Password for Level 18

Once inside Bandit17:

```bash
cat /etc/bandit_pass/bandit17
```

---

## ✅ Summary

| Step | Description |
|------|-------------|
| 1 | Scan all ports using `nmap -sV` |
| 2 | Identify SSL-enabled services |
| 3 | Submit password to SSL service using `openssl s_client` |
| 4 | Extract and store the SSH private key |
| 5 | `chmod 600` the key and login via `ssh -i` |
| 6 | Use `cat` to retrieve next level's password |

---
