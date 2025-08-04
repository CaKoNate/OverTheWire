# 🏴 Bandit Level 32 → Level 33

## 🎯 Level Goal

After all this Git stuff, it’s time for another **escape challenge**.

> 🔐 The password for `bandit32` is the one you obtained at the end of **Level 31**.

---

## 🛠️ Commands You May Need

```
sh, man, $0
```

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: SSH into bandit32

```bash
ssh bandit32@bandit.labs.overthewire.org -p 2220
```

Use the password from the previous level.

---

### 🔹 Step 2: Observe the custom shell

After logging in, you’ll see:

```bash
Welcome to the shell!
$
```

This is a **restricted shell**, and standard commands (like `ls`, `cat`, `pwd`) won’t work here.

---

### 🔹 Step 3: Escape the shell

Type:

```bash
$0
```

> `$0` is a shell variable that contains the name of the shell you're using. Executing it invokes the shell directly.

Once you do this, you'll escape into a standard shell prompt like:

```bash
$ /bin/sh
```

Now you can use normal commands again.

---

### 🔹 Step 4: Read the password

After escaping, run:

```bash
cat /etc/bandit_pass/bandit33
```

Copy the output. This is the password for **bandit33**.

---

## 🧠 Notes

- If you're still stuck in the limited shell, double-check you typed `$0` correctly.
- You can verify you escaped if `ls`, `whoami`, etc., begin to work.

---

