# 🏴 Bandit Level 31 → Level 32

## 🎯 Level Goal

There is a **Git repository** located at:

```
ssh://bandit31-git@localhost/home/bandit31-git/repo
```

Connect via **port 2220**, **clone the repository**, and follow the instructions inside the `README.md` file to push a specific file to the repository.

> 🔐 The password for `bandit31-git` is the same as the password for `bandit31`.

---

## 🛠️ Commands You May Need

```
git, git add, git commit, git push, echo
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into bandit31

```bash
ssh bandit31@bandit.labs.overthewire.org -p 2220
```

Use the password obtained from **Level 30**.

---

### 🔹 Step 2: Clone the Git repository

```bash
git clone ssh://bandit31-git@localhost:2220/home/bandit31-git/repo
cd repo
```

---

### 🔹 Step 3: Read the instructions

```bash
cat README.md
```

You should see:

```
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master
```

---

### 🔹 Step 4: Create the file

```bash
echo 'May I come in?' > key.txt
```

---

### 🔹 Step 5: Add and commit the file

```bash
git add key.txt
git commit -m "Add key.txt with required content"
```

---

### 🔹 Step 6: Push the file

```bash
git push origin master
```

Enter the password for `bandit31-git` when prompted (same as `bandit31`).

---

### 🏁 Final Step: Get the password for bandit32

After pushing successfully, the server should immediately output:

```bash
The password for bandit32 is: <password>
```

🎉 Use this password to login as **bandit32**.

---

## 🧠 Notes

- This level tests basic **Git push** mechanics.
- You must commit to the correct **branch (`master`)**.
- Be sure the file is named **exactly** `key.txt` and contains the **exact phrase** `'May I come in?'`.

---

## ✅ Completion

You’ve now completed **all 32 levels** of the **Bandit** wargame! 🎓

### ➕ What’s Next?

- Try other OverTheWire games: `Narnia`, `Leviathan`, `Behemoth`, etc.
- Move on to beginner-friendly CTFs like [PicoCTF](https://picoctf.org/) or [TryHackMe](https://tryhackme.com/).
