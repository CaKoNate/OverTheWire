# Bandit Level 1 → Level 2

## 📜 Level Goal
The password for the next level is stored in a file called `-` located in the home directory.  
This challenge focuses on handling filenames that start with a dash (`-`), which can cause commands to misinterpret them as options.

## 🛠 Useful Commands
`ls`, `cd`, `cat`, `file`, `du`, `find`

---

## 🚀 Solution Steps

1. **List files in the home directory**:
    ```bash
    ls -la
    ```
    You will see a file named:
    ```
    -
    ```
    It starts with a **dash**.

2. **Understand the problem**:
   - Filenames starting with `-` are often interpreted as **command options**.
   - To avoid this, you can:
     - Use `./` before the filename.
     - Or use `--` to indicate the end of options.

3. **Read the file contents**:  
    ```bash
    cat ./-
    ```
    or:
    ```bash
    cat -- -
    ```

4. **Copy the password**  
   The output will be the password for the next level. Copy it and log in to Bandit Level 2.

---

## 💡 Key Learning Points
- Prefix `./` to a filename to reference it explicitly in the current directory.
- Use `--` to signal the end of command options, ensuring that filenames starting with `-` are treated correctly.
- Always use `ls -la` to view all files, including those with tricky names.
