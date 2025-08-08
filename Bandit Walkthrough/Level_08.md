```markdown
# Bandit Level 8 → Level 9

## 📝 Level Goal
The password for the next level is stored in the file `data.txt` and is the **only line of text that occurs only once**.

## 🛠️ Useful Commands
`cat`, `sort`, `uniq`

---

## 🚀 Solution Steps

1. **Go to the home directory** (usually you are already there after login):
   ```bash
   cd ~
   ```

2. **Sort the file and find the unique line**:
   ```bash
   sort data.txt | uniq -u
   ```

   - `sort` sorts all the lines in the file (required for `uniq` to work correctly).
   - `uniq -u` prints only lines that appear **exactly once**.

3. **Copy the output** — this single line is the password for the next level.

---

## ✅ Example

If `data.txt` contains:
```
abc
123
xyz
abc
123
```

Running:
```bash
sort data.txt | uniq -u
```

Will output:
```
xyz
```

`xyz` is the password for the next level.

---

## 🔐 Note
- Always run `sort` before `uniq`, or `uniq` will only check for adjacent duplicates.
- In this level, there is exactly **one** unique line — the password.
```
