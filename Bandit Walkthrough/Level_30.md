# 🏴 Bandit Level 30 → Level 31

## 🎯 Level Goal

There is a **Git repository** located at:

```
ssh://bandit30-git@localhost/home/bandit30-git/repo
```

You must connect through port `2220`, **clone the repository**, and find the password for the next level.

> 🔐 The password for `bandit30-git` is the same as the password for `bandit30`.

---

## 🛠️ Commands You May Need

```
git, ls, cat, git log, git show, git tag
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into bandit30

```bash
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

Use the password obtained from **Level 29**.

---

### 🔹 Step 2: Clone the Git repository

```bash
git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
```

Enter the same password used for `bandit30` when prompted.

---

### 🔹 Step 3: Inspect the repository

```bash
cd repo
ls -la
```

There may not be obvious files shown. Let’s dig deeper.

---

### 🔹 Step 4: List tags

This level hides the password in a **tag**, not in files or branches.

```bash
git tag
```

You should see a tag like:

```
secret
```

---

### 🔹 Step 5: Show the tag content

```bash
git show secret
```

This will display the commit message associated with the `secret` tag, and you’ll find the password inside.

---

## 🔐 Login to Next Level

```bash
ssh bandit31@bandit.labs.overthewire.org -p 2220
```

Use the password you just retrieved.

---

## 🧠 Notes

- While Level 29 used a **branch**, this level uses a **tag** to hide the password.
- Use `git tag` and `git show` to retrieve information hidden in Git tags.

