# 🏴 Bandit Level 17 → Level 18

---

## 🎯 Level Goal

> There are 2 files in the home directory: `passwords.old` and `passwords.new`.  
> The password for the next level is in `passwords.new` and is the **only line that has been changed** compared to `passwords.old`.

---

## 🛠 Commands You May Need

```bash
diff, grep, comm, cmp
```

---

## 🧭 Step-by-Step Instructions

### 📁 Step 1: List the Files

Once logged in to `bandit17`, check the files:

```bash
ls
```

You should see:

```text
passwords.new  passwords.old
```

---

### 🧪 Step 2: Compare the Files Using `diff`

Use the `diff` command to find the **difference between the two files**:

```bash
diff passwords.old passwords.new
```

Sample output:

```text
42c42
< abcdefghijklmnopqrst
---
> xly0qrbiarea3nqy9wzq5g7bbfj5n2g7
```

The line starting with `>` is the **new password** in `passwords.new`.

#### ⚠️ **Important Note:**

> ❗ If you reverse the file order like this:

```bash
diff passwords.new passwords.old
```

You will still get an output, but the `<` and `>` signs will be **inverted**. This can confuse you into thinking the wrong line is the new password.  
If you use the wrong line, it may cause problems or delays in the next lab (`bandit18`), especially since the next level has built-in traps like auto logout.

---

## ✅ Summary

| Step | Description |
|------|-------------|
| 1 | List files: `ls` |
| 2 | Use `diff passwords.old passwords.new` or `grep` |
| 3 | Extract the changed line |
| 4 | Log in to `bandit18` using the password |

---
