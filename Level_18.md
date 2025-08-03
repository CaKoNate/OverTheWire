# 🏴 Bandit Level 18 → Level 19

---

## 🎯 Level Goal

> The password for the next level is stored in a file named `readme` in the home directory.  
> Unfortunately, someone has modified `.bashrc` to **log you out immediately** when you log in with SSH.

---

## 💡 Problem

Every time you log in to `bandit18`, it instantly logs you out — this is due to a malicious command added in the `.bashrc` file.  
You need to **bypass the `.bashrc` execution** to stay logged in.

---

## 💻 Recommended Terminals

| Tool                        | Supported | Notes             |
|----------------------------|-----------|-------------------|
| ✅ Terminal (Linux/macOS)   | ✔         | Ideal             |
| ✅ Git Bash / WSL (Windows) | ✔         | Recommended       |
| ✅ PowerShell (Windows)     | ✔         | Usable            |

---

## 🧭 Step-by-Step Instructions

### 🛑 Step 1: Bypass `.bashrc` Auto Logout

Instead of logging in normally, pass a command directly via SSH to prevent `.bashrc` from running:

```bash
ssh bandit.labs.overthewire.org -p 2220 -l bandit18 "bash --noprofile"
```

- The `bash --noprofile` command launches a shell **without executing `.bashrc`** or `.profile`, which avoids the logout trap.

---

### 📁 Step 2: Find the Password File

Once logged in, list the contents of the home directory:

```bash
ls
```

You should see:

```text
readme
```

---

### 📖 Step 3: Read the Password

To view the password for the next level:

```bash
cat readme
```

This will output the password for **Bandit Level 19**.

---

## ✅ Summary

| Step | Description |
|------|-------------|
| 1 | Use SSH with `bash --noprofile` |
| 2 | Run `ls` to find the `readme` file |
| 3 | Run `cat readme` to read the password |

---
