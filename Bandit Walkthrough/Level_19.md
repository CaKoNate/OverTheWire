# 🏴 Bandit Level 19 → Level 20

---

## 🎯 Level Goal

> To gain access to the next level, you should use the **setuid binary** in the home directory.  
> Execute it **without arguments** to find out how to use it.  
> The password for the next level is stored in the usual place:  
> `/etc/bandit_pass/bandit20` — **but you'll only be able to read it after running the binary**.

---

## 🔍 What is a SetUID Binary?

A SetUID binary is a special kind of executable that runs with the **permissions of the file’s owner**, not the user who runs it.  
In this case, the file is owned by `bandit20`, which means running it properly may grant you access to read their password file.

---

## 🧭 Step-by-Step Instructions

### 📁 Step 1: Navigate to the Home Directory

Once logged in as `bandit19`, you'll see a file (e.g., `bandit20-do`):

```bash
ls -l
```

Sample output:
```text
-rwsr-x--- 1 bandit20 bandit19 7403 May  7  2020 bandit20-do
```

Note:
- The `s` in `-rwsr-x---` indicates it’s a SetUID binary.
- It's owned by `bandit20`.

---

### ▶️ Step 2: Run the Binary without Arguments

```bash
./bandit20-do
```

Output will be:
```text
Run a command as another user.
Usage: ./bandit20-do <command>
```

This confirms that the binary lets you run a command as user `bandit20`.

---

### 🔑 Step 3: Use it to Read the Password File

Now run the command below to retrieve the password for the next level:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

You should now see the password for **Bandit Level 20** printed in your terminal.

---

## ✅ Summary

| Step | Command |
|------|---------|
| View files in home directory | `ls -l` |
| Run binary with no args | `./bandit20-do` |
| Get password | `./bandit20-do cat /etc/bandit_pass/bandit20` |

---

## 🧠 Notes

- Do **not** use `sudo` or other privilege escalation tools — the SetUID binary already runs with elevated permissions.
- Ensure you type the file name and path exactly.

---
