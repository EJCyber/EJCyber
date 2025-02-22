# Log Inspection via Event Viewer

## Overview
After setting up the honeypot VM, it's crucial to inspect the logs to detect and analyze attack patterns. This guide explains how to use **Event Viewer** to check security-related events.

## Prerequisites
- A **Honeypot VM** running in **Azure**.
- **RDP** access to the VM.
- Basic understanding of **Event Viewer** and Windows Security Logs.


## Steps

### 1️⃣ Access Event Viewer
1. Log into your **Honeypot VM** using **Remote Desktop**.
2. Press `Win + R`, type **`Event Viewer`**, and hit **Enter**.
3. In the **Event Viewer**, expand **Windows Logs**, then click **Security**.
![image](https://github.com/user-attachments/assets/737f2a35-19b0-4296-8a90-bb38cdd50028)

### 2️⃣ Filter for Failed Logins
1. In the **Actions** pane, click **Filter Current Log**.
2. In the **Event ID** field, type **4625** (this represents failed login attempts).
3. Click **OK** to filter for these events.
![image](https://github.com/user-attachments/assets/78b2a15e-e55a-44dc-bd4f-81b236002e77)

### 3️⃣ Analyze Logs
Review the logs for suspicious patterns, such as multiple failed login attempts from different IPs, which could indicate a brute-force attack.


## 🎯 Next Steps
✅ Proceed to **Set up Log Analytics** to forward logs and enhance your analysis.

🚀 Check out [Log Forwarding, Log Analytics, and KQL Queries](log-forward-kql.md) guide.
