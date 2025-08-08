# Bandit Level 2 → Level 3

## 📜 Level Goal
The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.  
This challenge focuses on handling filenames with spaces and special characters that can cause issues when using commands in the terminal.

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
    --spaces in this filename--
    ```
    It contains **spaces** and **leading dashes**.

2. **Understand the problem**:
   - **Spaces in filenames** must be escaped with `\` or enclosed in quotes `" "`.
   - **Leading dashes** (`-`) can be interpreted as command options, so they must be handled carefully.

3. **Read the file contents**:  

   – Ending command options with `--`:**
    ```bash
    cat -- "--spaces in this filename--"
    ``` 

4. **Copy the password**  
   The output will be the password for the next level. Copy it and log in to Bandit Level 3.

---

## 💡 Key Learning Points
- Use **quotes** or **backslashes** to handle filenames with spaces.
- Use `--` to indicate the end of command options when dealing with filenames that start with `-`.
- Always list files with `ls -la` to see hidden files and unusual filenames.
