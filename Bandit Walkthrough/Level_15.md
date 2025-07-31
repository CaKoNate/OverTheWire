Bandit Level 15 → Level 16
🔑 Level Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL/TLS encryption.

🛠️ Tools You May Need
openssl s_client, ssh

🔄 Step-by-Step Instructions
1️⃣ Step 1: Open SSL connection to the target port
Simply run the following command:

```bash
openssl s_client -connect localhost:30001
```
When prompted, manually type the password for Bandit Level 15 and press Enter.

2️⃣ Step 2: Receive the Next Password
After submitting the password, the server will return the password for Bandit Level 16.

🟢 What This Does:
Establishes an encrypted SSL connection to localhost:30001

Waits for your input (the current password)

Sends it securely and receives the next password in response

⚠️ Notes
If you see messages like DONE, RENEGOTIATING, or KEYUPDATE, refer to the CONNECTED COMMANDS section in the man s_client.

Press Ctrl+C after receiving the password to exit the SSL session.