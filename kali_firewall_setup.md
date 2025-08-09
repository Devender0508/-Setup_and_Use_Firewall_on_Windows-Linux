# 🛡️ Kali Linux Firewall Configuration with UFW - Cybersecurity Internship

## 🎯 Objective
Configure and test basic firewall rules using **UFW** (Uncomplicated Firewall) in Kali Linux, and understand how firewall rules filter network traffic.

---

## 🛠 Tools Used
- 🐧 **Kali Linux 2025.x**
- 🔥 **UFW** (Uncomplicated Firewall)
- 📟 **Terminal**
- 🔌 **Telnet Client** (for testing)

---

## 📋 Steps Performed

### **Step 1 – Install UFW (if not already installed)**
```bash
sudo apt update
sudo apt install ufw -y
```
**[Screenshot](screenshots/):** install_ufw.png`

---

### **Step 2 – Enable or Disable the Firewall**
- **Enable UFW**:
```bash
sudo ufw enable
```
- **Disable UFW**:
```bash
sudo ufw disable
```
- **Check Status**:
```bash
sudo ufw status verbose
```
**[Screenshot](screenshots/):** enable_disable_status.png`

---

### **Step 2.1 – Allow SSH (Port 22)**
```bash
sudo ufw allow 22/tcp
```
**[Screenshot](screenshots/):** allow_ssh.png`

💡 **Note:**  
If you are configuring UFW on a **remote Kali system**, this step is **critical** to avoid losing your SSH connection.  
UFW blocks incoming connections by default, so adding this rule ensures that remote access remains available.

---

### **Step 3 – List Current Firewall Rules**
```bash
sudo ufw status numbered
```
**[Screenshot](screenshots/):** list_rules.png`

**Example Output (Before Adding Rules):**
```plaintext
Status: active

     To                         Action      From
     --                         ------      ----
```

---

### **Step 4 – Block a Specific Port (Telnet – 23)**
```bash
sudo ufw deny 23/tcp
```
**[Screenshot](screenshots/):** block_port23.png`

**Example Output (After Blocking Port 23):**
```plaintext
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW       Anywhere
[ 2] 22/tcp (v6)                ALLOW       Anywhere (v6)
[ 3] 23/tcp                     DENY        Anywhere
[ 4] 23/tcp (v6)                DENY        Anywhere (v6)
```

---

### **Step 5 – Test the Block Rule**
1. Install Telnet Client (if not installed):
```bash
sudo apt install telnet -y
```
2. Try to connect:
```bash
telnet localhost 23
```
You should see **"Connection refused"** (blocked by firewall).

**[Screenshot](screenshots/):** telnet_test.png`

---

### **Step 6 – Remove the Test Block Rule**
- List rules with numbers:
```bash
sudo ufw status numbered
```
- Delete the rule by its number (example: rule 3):
```bash
sudo ufw delete 3
sudo ufw delete 4
```
**[Screenshot](screenshots/):** remove_rule.png`

**Example Output (After Removing the Rule):**
```plaintext
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22/tcp                     ALLOW       Anywhere
[ 2] 22/tcp (v6)                ALLOW       Anywhere (v6)
```

---

## 📜 Summary: How UFW Filters Traffic
- **UFW** is a simple frontend for `iptables`.
- Works by defining rules to **allow** or **deny** traffic.
- Rules can be based on:
  - **Port**
  - **Protocol**
  - **IP address**
- Default policy:
  - **Deny incoming**
  - **Allow outgoing**
- Easy to use with `allow`, `deny`, and `delete` commands.

---

## 📂 Deliverables
- **Screenshots folder**: `screenshots/`
  - `install_ufw.png`
  - `enable_disable_status.png`
  - `allow_ssh.png`
  - `list_rules.png`
  - `block_port23.png`
  - `telnet_test.png`
  - `remove_rule.png`


---



---
