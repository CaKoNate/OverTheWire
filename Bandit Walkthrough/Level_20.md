# 🏴 Bandit Level 20 → Level 21

---

## 🎯 Level Goal

> There is a **SetUID binary** in the home directory that:
> - Connects to **localhost** on the port you specify as a command-line argument.
> - Reads a line of text from the connection.
> - Compares it with the **password from the previous level (bandit20)**.
> - If the password is correct, it will send back the **password for bandit21** over the same connection.

🧠 **Hint**: Try running your own local network service (daemon) and make the binary connect to it.

---

## 🔧 Useful Commands

You may need the following:

- `ssh`, `cat`, `nc`
- `bash`, `screen`, `tmux`
- Unix job control: `&`, `bg`, `fg`, `jobs`, `CTRL-Z`

---

## 🧭 Step-by-Step Guide

### 📁 Step 1: Explore Home Directory

After logging in as `bandit20`, list files:

```bash
ls -l
```

Expected output:
```text
-rwsr-x--- 1 bandit21 bandit20 7303 May  7  2020 suconnect
```

This binary will be used to connect to a port you specify and send a response.

---

### 📄 Step 2: Get the Password of Bandit20

We need this password to feed into the connection:

```bash
cat /etc/bandit_pass/bandit20
```

Copy the output — you will need to send this via `nc`.

---

### 🔌 Step 3: Run a Local Netcat Server

In one terminal (or pane in `tmux` or `screen`), run:

```bash
nc -l -p 40000
```

This opens a server on port 40000 that waits for input and sends back a response.

---

### ▶️ Step 4: Run the Binary to Connect to the Server

Open a second terminal/tab (or background the `nc` process using `CTRL-Z` then `bg`) and run:

```bash
./suconnect 40000
```

This tells the binary to connect to your `nc` listener on port 40000.

---

### 📥 Step 5: Enter the Password in Netcat

In the `nc` terminal, after the connection is established, **paste the password from bandit20** and press **Enter**.

If correct, the response will be the **password for bandit21**.

---

## ✅ Summary

| Step | Action |
|------|--------|
| Check binary | `ls -l` |
| Read bandit20 password | `cat /etc/bandit_pass/bandit20` |
| Start listener | `nc -l -p 40000` |
| Run SetUID binary | `./suconnect 40000` |
| Paste password | (In `nc` window) paste password and press Enter |

---

## 🧠 Tips

- If you're stuck with one terminal, use `CTRL-Z` to pause the first process, then run the next.
- `tmux` or `screen` allows managing multiple terminals within a single SSH session.
- Make sure the port you pick is above 1024 (e.g., `40000`) — ports below that require root.

---

## 📌 Example Session (Simplified)

1. Terminal 1:
   ```bash
   nc -l -p 40000
   ```
2. Terminal 2:
   ```bash
   ./suconnect 40000
   ```
3. Terminal 1 (after connection):
   ```
   <paste bandit20 password>
   ```
   Output:
   ```
   xxxxxxxxxxxxxxx ← Password for Bandit21
   ```
