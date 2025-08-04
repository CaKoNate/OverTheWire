# 🏴 Bandit Level 28 → Level 29

## 🎯 Level Goal

There is a **Git repository** located at:

```
ssh://bandit28-git@localhost/home/bandit28-git/repo
```

You must **clone the repository** via port `2220` and **find the password** for the next level.

> 🔐 The password for `bandit28-git` is the same as the password for `bandit28`.

---

## 🛠️ Commands You May Need

```
git, ls, cat, git log, git checkout
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into `bandit28`

```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```

Enter the password you got from **Level 27**.

---

### 🔹 Step 2: Clone the Git repository

Inside the bandit server, run:

```bash
git clone ssh://bandit28-git@localhost:2220/home/bandit28-git/repo
```

You will be prompted for the password — enter the same one used for `bandit28`.

---

### 🔹 Step 3: Inspect the repository

Move into the cloned folder:

```bash
cd repo
ls -la
```

Check for existing files. In this level, the main clue is usually hidden in the Git history.

---

### 🔹 Step 4: View commit history

```bash
git log
```

You may see multiple commits. Carefully read the commit messages and look for anything that sounds like it might contain a password (e.g., "remove password").

---

### 🔹 Step 5: Checkout older commit

Once you find the commit that contains the password, copy its hash (the long hex string) and checkout that version:

```bash
git checkout <commit-hash>
```

Then check the files again:

```bash
ls
cat README
```

✅ You should find the password for `bandit29` inside the file.

---

## 🔐 Login to Next Level

```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
```

Use the password found in the previous step.
