# 🏴 Bandit Level 25 → Level 26

## 🎯 Level Goal

Logging into `bandit26` from `bandit25` should be fairly easy…  
But the shell for user `bandit26` is not `/bin/bash`, but something else.  
Find out what it is, how it works, and how to break out of it.

> 💡 **Note for Windows users**:  
> Powershell is known to cause issues with this level. Use **Command Prompt**, **PuTTY**, or a proper **Linux terminal**.

---

## 🛠️ Commands You May Need

```
ssh, cat, more, vi, ls, id, pwd
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into bandit25

```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
```

Enter the password obtained from Level 24.

---

### 🔹 Step 2: Check what shell bandit26 uses

```bash
cat /etc/passwd | grep bandit26
```

Output should be something like:

```
bandit26:x:1026:1026::/home/bandit26:/usr/bin/showtext
```

👉 The login shell for `bandit26` is `/usr/bin/showtext`, which is **not** a typical shell.

---

### 🔹 Step 3: View the script at `/usr/bin/showtext`

```bash
cat /usr/bin/showtext
```

Expected output:

```bash
#!/bin/sh
more /home/bandit26/text.txt
```

📄 This means: when logging in as `bandit26`, it runs the `more` command on a text file instead of opening a normal shell.

---

### 🔹 Step 4: Break out of `more` using vi

🪄 **Important tip**: To **activate the `more` prompt**, **resize your terminal window** to a smaller size so that the file doesn't fit on the screen. This will cause `more` to display something like:

```
--More--(%)
```

When you see this:

1. Press `v`  
   → This opens the file in the `vi` editor.

2. In `vi`, type:
   ```
   :!bash
   ```
   → This escapes to a real bash shell!

---

### 🔹 Step 5: Use `bandit26-do` to get the password for level 27

Now that you're inside a real shell as `bandit26`, use the provided helper command to get the password for `bandit27`:

```bash
bandit26-do cat /etc/bandit_pass/bandit27
```

✅ This will output the password for level 27.

---

## 🔐 Login to Next Level

```bash
ssh bandit27@bandit.labs.overthewire.org -p 2220
```

---

## ⚠️ Additional Notes

- `more` only activates if the file overflows the terminal size. Resize your window **smaller** to force paging mode.
- Pressing `v` in `more` opens `vi`, and from there you can escape to a full shell.
- `bandit26-do` is a special command provided to run other commands as the next level user (similar to `sudo`).
