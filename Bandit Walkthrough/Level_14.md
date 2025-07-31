Bandit Level 14 → Level 15
🔑 Level Goal
The password for the next level can be retrieved by submitting the current level’s password to port 30000 on localhost.

🛠️ Tools You May Need
cat, nc (netcat), ssh

🔄 Step-by-Step Instructions
1️⃣ Step 1: Check the Current Password
If you need to recall the current password, run:

```bash
cat /etc/bandit_pass/bandit14
```

2️⃣ Step 2: Send the Password to Port 30000 via nc

```bash
cat /etc/bandit_pass/bandit14 | nc localhost 30000
```

🟢 What This Does:
Reads the current level password

Sends it to port 30000 on localhost

Receives the password for Level 15 in return