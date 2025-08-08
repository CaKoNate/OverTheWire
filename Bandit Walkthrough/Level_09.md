```markdown
# Bandit Level 9 → Level 10

## 📝 Level Goal
The password for the next level is stored in the file `data.txt` in one of the few **human-readable strings**, preceded by several `=` characters.

## 🛠️ Useful Commands
`strings`, `grep`

---

## 🚀 Solution Steps

1. **Go to the home directory** (usually you are already there after login):
   ```bash
   cd ~
   ```

2. **Extract human-readable strings from `data.txt`**:
   ```bash
   strings data.txt
   ```

3. **Filter only the lines containing `=`** (the password will appear after several `=` signs):
   ```bash
   strings data.txt | grep "=="
   ```

4. **Find the password**:
   - Look for the line that has the password right after multiple `=` characters.

---

## ✅ Example

If `data.txt` contains binary data with a hidden password like:
```
...random binary...
==========abc123password
...random binary...
```

The command:
```bash
strings data.txt | grep "=="
```

Will output:
```
==========abc123password
```

`abc123password` is the password for the next level.

---

## 🔐 Note
- `strings` extracts printable ASCII characters from binary or mixed files.
- Using `grep` helps narrow down the output to quickly locate the password.
```
