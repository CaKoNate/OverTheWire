```markdown
# Bandit Level 7 → Level 8

## 📝 Level Goal
The password for the next level is stored in the file `data.txt` **next to the word `millionth`**.

## 🛠️ Useful Commands
`cat`, `grep`

---

## 🚀 Solution Steps

1. **Go to the home directory** (usually you are already there after login):
   ```bash
   cd ~
   ```

2. **Search for the word `millionth` in the file**:
   ```bash
   grep "millionth" data.txt
   ```

3. **Identify the password**:
   - The password will be on the same line as the word `millionth`.
   - Example output might look like:
     ```
     millionth 123456789abcdef
     ```
     Here, `123456789abcdef` is the password for the next level.

---

## ✅ Example

If `data.txt` contains:
```
first abc123
millionth mypasswordhere
last xyz789
```

Running:
```bash
grep "millionth" data.txt
```

Will output:
```
millionth mypasswordhere
```

`mypasswordhere` is the password for the next level.

---

## 🔐 Note
- `grep` searches for matching patterns in a file.
- By default, it prints the entire line containing the match.
```
