# Honeypot Deployment Guide

## 📌 Overview
This guide explains how to deploy a honeypot in **Microsoft Azure** to attract and analyze real-world cyber threats.

## 🔧 Prerequisites
- **Microsoft Azure account** with a subscription ([Sign up here](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account))
- **Virtual Machine (VM)** setup permissions
- Basic knowledge of **firewall rules** and **networking**

## 🚀 Deployment Steps

### 1️⃣ Create a Virtual Machine (VM)
1. **Log in to Azure** and navigate to **Azure Virtual Machines**.
2. Click **Create** → **Virtual Machine**.
3. Choose:
   - **Operating System:** Windows 10 (or Server 2019 / Linux)
   - **Size:** Minimum 2 vCPUs, 4GB RAM
   - **Networking:** Allow RDP/SSH (but restrict access after setup)
4. Configure disk and click **Review + Create**.
5. Once deployed, **note the Public IP** of the VM.

### 2️⃣ Configure Firewall Rules to Simulate a Honeypot
1. In **Azure Portal**, go to **Networking** → **Inbound Port Rules**.
2. Create a rule to **allow all inbound traffic** for logging purposes.
3. Save settings and apply changes.
4. **Disable Windows Firewall**:
   - Open Run (`Win + R`), type `wf.msc`, and press Enter.
   - Set all profiles to **Off**.

### 3️⃣ Logging and Event Collection
1. Fail **3 login attempts** using a fake username like **“employee”**.
2. Log into your VM.
3. Open **Event Viewer** → Navigate to **Security Logs**.
4. Verify **Event ID 4625** appears for failed logins.

### 4️⃣ Next Steps
- Proceed to [Log Analytics Setup](log-analytics-setup.md) to centralize log collection.
- Continue to [Sentinel Integration](sentinel-integration.md) for SIEM analysis.

📩 **For any issues or enhancements, feel free to reach out!**