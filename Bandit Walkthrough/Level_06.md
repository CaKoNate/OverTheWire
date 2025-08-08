# Bandit Level 6 → Level 7

## 📝 Level Goal
The password for the next level is stored **somewhere on the server** and has all of the following properties:
- Owned by user `bandit7`
- Owned by group `bandit6`
- Exactly **33 bytes** in size

## 🛠️ Useful Commands
`find`, `cat`, `ls`, `stat`

---

## 🚀 Solution Steps

1. **Search for the file matching the conditions** (search from `/` for the whole system):
   ```bash
   find / -user bandit7 -group bandit6 -type f -size 33c 2>/dev/null
   ```
   - `-user bandit7` → file owned by user `bandit7`
   - `-group bandit6` → file owned by group `bandit6`
   - `-type f` → regular files only
   - `-size 33c` → exactly 33 bytes (`c` = bytes)
   - `2>/dev/null` → suppress “Permission denied” errors

   **Tip:** To speed up the search, if you know the likely location, replace `/` with a specific directory path, e.g. `~` or `/home`.

2. **Verify the file’s ownership and size**:
   ```bash
   ls -l /path/to/found_file
   stat /path/to/found_file
   ```

3. **Read the file to get the password**:
   ```bash
   cat /path/to/found_file
   ```
   The output will be a 33-character password for the next level.

---

## ✅ One-liner Solution
If you are confident there is only one matching file:
```bash
cat $(find / -user bandit7 -group bandit6 -type f -size 33c 2>/dev/null)
```

---

## 🔐 Notes
- The `2>/dev/null` part is important to hide the many “Permission denied” messages.
- `33c` means 33 **bytes**, not 33 characters in text (though here they match in count).
- Always verify ownership and size if multiple files are returned.

