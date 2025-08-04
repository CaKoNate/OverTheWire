```markdown
# Bandit Level 10 → Level 11

## 📝 Level Goal
The password for the next level is stored in the file `data.txt`, which contains **base64 encoded** data.

## 🛠️ Useful Commands
`cat`, `base64`, `grep`

---

## 🚀 Solution Steps

1. **Navigate to the home directory** (usually already there on login):
   ```bash
   cd ~
   ```

2. **View the content of `data.txt`**:
   ```bash
   cat data.txt
   ```

3. **Decode the base64 data**:
   ```bash
   cat data.txt | base64 -d
   ```

   Hoặc viết gọn:
   ```bash
   base64 -d data.txt
   ```

4. **Find the password** (look for a string resembling a password):
   The result will show the password in plain text. Copy it to use for Level 11.

---

## ✅ Example

If `data.txt` contains:
```
VGhpcyBpcyBteSBzZWNyZXQgcGFzc3dvcmQ=
```

After decoding:
```
This is my secret password
```

---

## 🔐 Note
Base64 encoding turns binary/text into printable ASCII characters. Use `base64 -d` to decode back to readable form.
```
