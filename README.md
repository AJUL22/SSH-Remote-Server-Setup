# Remote Linux Server & SSH Setup

## ✅ Project Objectives
- Deploy a remote Linux server on a cloud provider.
- Create two SSH key pairs and add them to the server.
- Successfully connect using both keys.
- Configure SSH aliases in `~/.ssh/config`.
- (Optional) Install Fail2Ban for security.

---

## 🚀 Steps Completed

### 1️⃣ Remote Server Setup
- Provider used: DigitalOcean / AWS / Other
- OS: Ubuntu 22.04 LTS
- Server IP: `{YOUR_SERVER_IP}`

### 2️⃣ Created Two SSH Keys
```bash
ssh-keygen -t ed25519 -C "key1"
ssh-keygen -t ed25519 -C "key2"

### 3️⃣ Added Public Keys to Server
ssh-copy-id -i ~/.ssh/key1.pub {YOUR_USERNAME}@{YOUR_SERVER_IP}
ssh-copy-id -i ~/.ssh/key2.pub {YOUR_USERNAME}@{YOUR_SERVER_IP}

### 4️⃣ Verified SSH Access
ssh -i ~/.ssh/key1 {YOUR_USERNAME}@{YOUR_SERVER_IP}
ssh -i ~/.ssh/key2 {YOUR_USERNAME}@{YOUR_SERVER_IP}


### 5️⃣ SSH Config with Alias

Host myserver
    HostName {YOUR_SERVER_IP}
    User {YOUR_USERNAME}
    IdentityFile ~/.ssh/key1

sudo apt update && sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban


