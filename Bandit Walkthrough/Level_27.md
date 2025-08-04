# 🏴 Bandit Level 27 → Level 28

## 🎯 Level Goal

There is a **Git repository** hosted at:

```
ssh://bandit27-git@localhost/home/bandit27-git/repo
```

You need to **clone the repository** using port `2220`, and **find the password** for the next level inside it.

> 🔐 The password for `bandit27-git` is the same as the password for `bandit27`.

---

## 🛠️ Commands You May Need

```
git, ssh, ls, cat
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into `bandit27`

```bash
ssh bandit27@bandit.labs.overthewire.org -p 2220
```

Enter the password obtained from Level 26.

---

### 🔹 Step 2: Clone the Git repository

To clone using SSH with a custom port (2220), use this command **from inside the bandit server**:

```bash
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
```

You’ll be prompted for a password — enter the same one used for `bandit27`.

---

### 🔹 Step 3: Check the contents

Once cloned, enter the repo directory:

```bash
cd repo
ls -a
```

Look for common Git files like `.git`, `README`, etc.

---

### 🔹 Step 4: Read the file

Usually the password is inside a `README` file or similar. Try:

```bash
cat README
```

✅ The file should contain the password for `bandit28`.

---

## 🔐 Login to Next Level

```bash
ssh bandit28@bandit.labs.overthewire.org -p 2220
```

Use the password you just found.
