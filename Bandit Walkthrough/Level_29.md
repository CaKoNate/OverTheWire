# 🏴 Bandit Level 29 → Level 30

## 🎯 Level Goal

There is a **Git repository** hosted at:

```
ssh://bandit29-git@localhost/home/bandit29-git/repo
```

Connect via port `2220`, **clone the repository**, and find the password for the next level.

> 🔐 The password for `bandit29-git` is the same as the password for `bandit29`.

---

## 🛠️ Commands You May Need

```
git, ls, cat, git branch, git checkout, git log, git show
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Log into bandit29

```bash
ssh bandit29@bandit.labs.overthewire.org -p 2220
```

Enter the password obtained from **Level 28**.

---

### 🔹 Step 2: Clone the Git repository

Inside the Bandit shell, run:

```bash
git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
```

Enter the same password used for `bandit29`.

---

### 🔹 Step 3: Explore the repository

Navigate into the repo:

```bash
cd repo
ls -la
```

There may not be anything visible at first.

---

### 🔹 🔀 **Important: Check available branches**

Unlike levels 27 and 28 (which use tags or visible files), this level hides the password in another **branch**.

List all branches:

```bash
git branch -a
```

You may see something like:

```
* master
  dev
```

The branch named `dev` is a development branch created by the developers.

---

### 🔹 Step 4: Switch to the dev branch

```bash
git checkout dev
```

Check the files again:

```bash
ls
cat README
```

✅ The password for **bandit30** is usually inside the `README` file or another file on this branch.

---

## 🔐 Login to Next Level

```bash
ssh bandit30@bandit.labs.overthewire.org -p 2220
```

Use the password found in the `dev` branch.

---

## 🧠 Notes

- **This level is different from 27 and 28**, which rely on `git log` or `git show`.
- Here, you must understand **Git branches** and how to switch to a different one (`checkout`) to find hidden data.

