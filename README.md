# Setup_and_Use_Firewall_on_Windows-Linux
# 🔐 Windows Firewall Configuration & Testing

## 🎯 Objective
Configure and test basic firewall rules to allow or block traffic in **Windows**, and understand how Windows Defender Firewall filters network traffic.

---

## 🛠 Tools Used
- 🖥️ **Windows 10/11**
- 🛡️ **Windows Defender Firewall with Advanced Security** (built-in)
- 📟 **Command Prompt** (for testing)
- 🔌 **Telnet Client** (for connection testing)

---

## 📋 Steps Performed

### **Step 1 – Enable or Disable Windows Defender Firewall (Command Prompt)**

**Open Command Prompt as Administrator** (Search for `cmd`, right-click, select **Run as administrator**).

- **Enable Firewall for All Profiles**:
```cmd
netsh advfirewall set allprofiles state on
```

- **Disable Firewall for All Profiles**:
```cmd
netsh advfirewall set allprofiles state off
```

📸 **Screenshot:** 
---

### **Step 2 – Open the Windows Firewall Configuration Tool**
1. Press **`Windows + R`**, type:
```
wf.msc
```
and press **Enter**.
2. This opens **Windows Defender Firewall with Advanced Security**.

📸 **Screenshot:**

---

### **Step 3 – List Current Firewall Rules**
1. In the left panel, click **Inbound Rules**.
2. Scroll to see all existing rules (Allowed / Blocked).

📸 **Screenshot:**

---

### **Step 4 – Add a Rule to Block a Specific Port (Example: Telnet Port 23)**
1. **Inbound Rules → New Rule…**
2. Select **Port** → Click **Next**.
3. Choose **TCP**, type `23` in **Specific local ports** → **Next**.
4. Select **Block the connection** → **Next**.
5. Check **Domain**, **Private**, and **Public** profiles → **Next**.
6. Name the rule (e.g., `Block Telnet Port 23`) → **Finish**.

📸 **Screenshot:** 

---

### **Step 5 – Test the Rule**
1. Install Telnet Client (if not already installed):
```cmd
dism /online /Enable-Feature /FeatureName:TelnetClient
```
2. In **Command Prompt**:
```cmd
telnet 127.0.0.1 23
```
3. You should see: **"Could not open connection"** (blocked).

📸 **Screenshot:**

---

### **Step 6 – Remove the Test Block Rule**
1. Go back to **Inbound Rules**.
2. Right-click on `Block Telnet Port 23` → **Delete** (or Disable).

📸 **Screenshot:** 

---

## 📜 Summary: How Windows Firewall Filters Traffic
- Filters **inbound** and **outbound** connections.
- Uses rules based on:
  - **Program** (application-based)
  - **Port** (TCP/UDP)
  - **Protocol** (HTTP, FTP, etc.)
  - **IP Address** (specific or range)
- **Allow** rules let traffic through.
- **Block** rules stop unwanted or risky connections.

---

## 📂 Deliverables
- **Screenshots folder**:
  **windows section**

---

## ✅ Outcome
- Learned to **enable/disable** Windows Defender Firewall from **Command Prompt**.
- Created and tested **custom port block rule**.
- Verified firewall functionality by simulating blocked connections.


---
