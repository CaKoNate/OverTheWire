# Bandit Level 4 → Level 5

## 📝 Level Goal
The password for the next level is stored in **the only human-readable file** inside the `inhere` directory.  
Tip: If your terminal output becomes messy, use the `reset` command.

## 🛠️ Useful Commands
`ls`, `cd`, `cat`, `file`, `du`

---

## 🚀 Solution Steps

1. **Navigate to the `inhere` directory**:
   ```bash
   cd ~/inhere
   ```

2. **Identify the human-readable file**:
   ```bash
   file ./*
   ```
   - The `file` command shows the type of each file.
   - Look for the one that says `ASCII text` (or similar) — this is the human-readable file.

3. **Read the contents of that file**:
   ```bash
   cat ./<readable_filename>
   ```
   The output is the password for the next level.

---

## ✅ Example

If `file ./*` outputs:
```
./file01: data
./file02: ASCII text
./file03: data
```

Then:
```bash
cat ./file02
```

Might output:
```
12345password67890
```

This is the password for the next level.

---

## 🔐 Notes
- The `inhere` directory may contain many files, but only **one** is human-readable.
- `file` is the most efficient way to detect which one it is.
