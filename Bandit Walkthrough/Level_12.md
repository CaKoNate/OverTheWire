# Bandit Level 12 Walkthrough

## 🌟 Goal
Find the password for the next level, hidden inside the `data.txt` file. This file:

- Is a hexdump of a binary file.
- Has been compressed multiple times with different formats (gzip, bzip2, tar, etc.).

---

## 🛠️ Required Tools
- `bash`
- Commands: `xxd`, `file`, `mkdir`, `cp`, `mv`, `gunzip`, `bunzip2`, `tar`, `strings`

---

## 🔄 Solution Steps

### 1. Create a temporary working directory
First, check for the `data.txt` file in your home directory:

```bash
ls -la ~
```

Then create and move into a temp directory:

```bash
temp_dir=$(mktemp -d)
echo "Temporary directory: $temp_dir"
cd $temp_dir
```

---

### 2. Copy and convert the hexdump to a binary file

```bash
cp ~/data.txt .
xxd -r data.txt > binary_file
```

---

### 3. Loop: Detect file format and decompress

Repeat the following steps until you reach a readable ASCII file:

#### ✔️ Identify file type:
```bash
file binary_file
```

#### ✏️ Rename file if needed:
```bash
mv binary_file <new_name>
```

#### 📁 Decompress accordingly:
```bash
# For gzip
gunzip file

# For bzip2
bunzip2 file

# For tar
tar -xf file
```

🔹 If `bunzip2` shows a filename error, it creates a file named `*.out`. Just rename it back.

---

### 4. Find the password from ASCII file
When you reach a text file:
```bash
strings <file> | grep -Eo '[a-zA-Z0-9]{30,}'
```

---

## ⚠️ Notes
- Always check file format after each step using `file`.
- Use the correct tool for each format.
- Working in `/tmp` prevents clutter in your home directory.

---

## 📌 Key Takeaways
- `file` helps detect binary file formats.
- Learn how to recursively unpack multiple compression layers.
- Use `xxd -r` to revert from hexdump to binary.
- Safe temp working in `/tmp` keeps things clean.

---

