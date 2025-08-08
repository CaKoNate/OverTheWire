```markdown
# Bandit Level 5 → Level 6

## 📝 Level Goal
The password for the next level is stored in a file **somewhere under the `inhere` directory** and has all of the following properties:
- Human-readable
- 1033 bytes in size
- Not executable

## 🛠️ Useful Commands
`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🚀 Solution Steps

1. **Go to the `inhere` directory**:
   ```bash
   cd ~/inhere
   ```

2. **Find the file matching the conditions**:
   ```bash
   find . -type f -size 1033c ! -executable
   ```
   - `-type f` → look for regular files.
   - `-size 1033c` → exactly 1033 bytes (`c` = bytes).
   - `! -executable` → file is **not executable**.

3. **Check if the file is human-readable**:
   ```bash
   file ./<found_filename>
   ```
   If the output says something like “ASCII text,” it’s human-readable.

4. **View the content (password)**:
   ```bash
   cat ./<found_filename>
   ```
   This will display the password for the next level.

---

## ✅ Example

If `find` returns:
```
./maybehere/file2
```

You run:
```bash
cat ./maybehere/file2
```

Output:
```
picoCTF{example_password}
```

`picoCTF{example_password}` is the password for the next level.

---

## 🔐 Note
- You can combine steps 2 and 4 into one:
  ```bash
  cat $(find . -type f -size 1033c ! -executable)
  ```
- The `file` command is optional here since the challenge guarantees the file is human-readable.
```
