```markdown
# Bandit Level 11 → Level 12

## 📝 Level Goal
The password for the next level is stored in the file `data.txt`, where all lowercase (`a-z`) and uppercase (`A-Z`) letters have been rotated by 13 positions (ROT13).

## 🛠️ Useful Commands
`cat`, `tr`, `grep`

---

## 🚀 Solution Steps

1. **Navigate to the home directory** (usually already there on login):
   ```bash
   cd ~
   ```

2. **View the content of `data.txt`** (will be encoded with ROT13):
   ```bash
   cat data.txt
   ```

3. **Decode the content using `tr` and ROT13**:
   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```

4. **Search for the password** (optional):
   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' | grep -i "password"
   ```

---

## ✅ Example

If the file contains:
```
Guvf vf zl frperg cnffjbeq
```

After decoding:
```
This is my secret password
```

You can then extract and use the password for Level 12.

---

## 🔐 Note
ROT13 is symmetric — applying it twice will return the original text.
```
