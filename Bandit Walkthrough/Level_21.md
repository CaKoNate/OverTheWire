# 🏴 Bandit Level 21 → Level 22 – Step-by-Step Guide

---

## 🎯 Goal
Find the password for user `bandit22` by analyzing the cronjob that is automatically running on the system.

---

## 🧩 Step 1: Check the cronjobs

Run the following command to view the contents of the cronjob file for this level:

```bash
cat /etc/cron.d/cronjob_bandit22
```

🔎 **Expected output**:

```cron
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```

👉 This means that a script is executed by `bandit22` both on system reboot and every minute.

---

## 🧩 Step 2: View the script that the cronjob runs

Use this command:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

🔎 **Expected output**:

```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

📌 What it does:
- Changes the file permission of `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` to readable by everyone
- Writes the password of `bandit22` into that file
- Since the permission is `644`, you (as `bandit21`) can read it

---

## 🧩 Step 3: Read the temporary file to get the password

Simply run:

```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

🎉 **You will see the password for bandit22!**

---

## ⚠️ Notes

- If the file isn’t there yet, wait for 1 minute and try again — cron runs the job every minute.
- You don’t need to modify the cronjob or the script — just leverage the behavior.
- After retrieving the password, connect to the next level via SSH:

```bash
ssh bandit22@bandit.labs.overthewire.org -p 2220
```

---

✅ **Key Commands Summary**

| Purpose | Command |
|--------|---------|
| View cronjob | `cat /etc/cron.d/cronjob_bandit22` |
| View cron script | `cat /usr/bin/cronjob_bandit22.sh` |
| Read file with password | `cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` |
| SSH to next level | `ssh bandit22@bandit.labs.overthewire.org -p 2220` |

---

📘 **Relevant commands**: `cron`, `crontab`, `cat`, `chmod`, `tmp`, `bash`
