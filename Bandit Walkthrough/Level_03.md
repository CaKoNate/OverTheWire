# Bandit Level 3 → Level 4

## 📝 Level Goal
The password for the next level is stored in **a hidden file** inside the `inhere` directory.

## 🛠️ Useful Commands
`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🚀 Solution Steps

1. **Navigate to the `inhere` directory**:
   ```bash
   cd ~/inhere
   ```

2. **List all files including hidden ones**:
   ```bash
   ls -la
   ```
   - `-a` shows hidden files (those starting with a `.`).
   - `-l` shows detailed information.

3. **Identify the hidden file**:
   - Look for a file whose name starts with `.` (dot) and is not `.` or `..`.

4. **Read the hidden file to get the password**:
   ```bash
   cat .<hidden_filename>
   ```

---

## ✅ Example

If `ls -la` outputs:
```
drwxr-xr-x  2 bandit3 bandit3 4096 May  7 12:00 .
drwxr-xr-x 10 root    root    4096 May  7 12:00 ..
-rw-r--r--  1 bandit3 bandit3   33 May  7 12:00 .hidden
```

Then:
```bash
cat .hidden
```

Might output:
```
mypassword123
```

This is the password for the next level.

---

## 🔐 Notes
- Hidden files start with a `.` in Linux.
- You can also find hidden files using:
  ```bash
  find . -type f
  ```
