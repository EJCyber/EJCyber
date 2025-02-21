# Honeypot VM Setup in Azure

## Overview
This guide walks you through setting up a **Honeypot Virtual Machine (VM)** in **Microsoft Azure** to attract and monitor real-world cyber threats. By exposing the VM to the internet, we can collect security event logs and analyze attack patterns in a simulated SOC environment.

## Prerequisites
- An **Azure Subscription** (preferably the free tier)
- Basic knowledge of **Azure Portal**
- Familiarity with **Virtual Machines and Networking**

---

## 1️⃣ Create a Resource Group
A **Resource Group** organizes all related resources in Azure:
1. In the **Azure Portal** ([portal.azure.com](https://portal.azure.com)), search for **Resource Groups**.
   ![Azure-ReseourceGroup-Creation](https://github.com/user-attachments/assets/3b8019d7-5e62-44b5-a722-82c9a0e35440)

2. Click **Create** and enter the following details:
   - **Subscription**: Select your active subscription.
   - **Resource Group Name**: `RG-SOC-Lab` (or choose your own name).
   - **Region**: `East US 2` (or a region close to you).
3. Click **Review + Create**, then **Create**.

---

## 2️⃣ Create a Virtual Network (VNet)
The **VNet** allows communication between Azure resources:
1. In the **Azure Portal**, search for **Virtual Networks**.
   ![VirtualNetwork-creation](https://github.com/user-attachments/assets/101f8583-3bbb-4221-a9ca-1a6755a78a4d)

2. Click **Create** and enter the following details:
   - **Subscription**: Select your active subscription.
   - **Resource Group**: Select `RG-SOC-Lab` (or your chosen group).
   - **Name**: `Vnet-Soc-Lab`
   - **Region**: `East US 2` (must match your resource group).
3. Click **Review + Create**, then **Create**.

---

## 3️⃣ Deploy the Honeypot Virtual Machine (VM)
1. In the **Azure Portal**, search for **Virtual Machines**.
2. Click **Create > Azure Virtual Machine** and enter:
   - **Subscription**: Select your active subscription.
   - **Resource Group**: `RG-SOC-Lab`
   - **Virtual Machine Name**: `Corp-Net-East-1` (Avoid obvious names like "Honeypot").
   - **Region**: `East US 2`
![image](https://github.com/user-attachments/assets/7c1f531a-5b43-4eb2-8974-3f6aa6a09bfa)

   - **Image**: Windows 10
   - **Size**: Since we ar utilizing the free subscription we should only have 1 option available. (If you are using the pay as you go, try for something that isn't too costly to help minimize cost)
   - **Administrator Username**: Choose a secure name.
   - **Password**: Set a strong password. (one that you will easily remember as this is just a lab you don't have to go crazy with this. But Always remember when working in the production always keep th passwords strong and lengthy)
![image](https://github.com/user-attachments/assets/cf66284a-d9c1-4951-916c-8917ee25f97b)

3. Under **Inbound Port Rules**:
   - Select **Allow Selected Ports**
   - Open **RDP (3389) for Windows**.
4. Click **Review + Create**, then **Create**.
![image](https://github.com/user-attachments/assets/85241504-130b-42b3-b826-c528d562158f)


---

## 4️⃣ Configure Network Security Group (NSG) Rules
1. In the **Azure Portal**, navigate to **Networking** for `Corp-Net-East-1`.
![image](https://github.com/user-attachments/assets/0a170c08-8d6b-4058-b573-3fb7285f0bd7)

2. Click on the **Network Settings** linked to the VM.
3. Under **Inbound Security Rules**, add a new rule:
   - **Source**: Any
   - **Destination**: Virtual Machine
   - **Service**: Select `All` (to attract attacks)
   - **Action**: Allow
4. Click **Add** to apply the changes.
![image](https://github.com/user-attachments/assets/8dbca487-2179-48ff-b1f6-c907df23a083)

---

## 5️⃣ Disable Windows Firewall (For Windows VMs Only)
1. Log into the VM using **Remote Desktop (RDP)**.
2. Open **Windows Defender Firewall**:
   - Press `Win + R`, type `wf.msc`, and hit **Enter**.
3. Click **Windows Defender Firewall Properties**.
![image](https://github.com/user-attachments/assets/5cefe8d7-70d5-4573-9da6-d04c25f6d63c)

4. Set **Firewall State** to `Off` for all profiles (Domain, Private, Public).
![image](https://github.com/user-attachments/assets/2ccf6919-89e6-47ad-bab1-c2da721f0ea5)

5. Click **Apply** and **OK**. (It should take up to 20min-1hour to start seeing activity in the raw events log)
6. Open **Event Viewer**
   - Press `Win + R`, type `Event Viewer`, and hit **Enter**
   - Click the **Windows Logs** dropdown
   - Click **Security** (Give it some time to load, it will begin to show all security related events that have occured on that machine so far. Take some time to observer this raw data)
![image](https://github.com/user-attachments/assets/737f2a35-19b0-4296-8a90-bb38cdd50028)

**Bonus tip:** If you Navigate to **Actions** on the right pane, click **Filter Current Log**, edit the text box that says **ALL Event IDs** and type **4625** (this event ID signifies a failed log in attempt), then click ok, you will see all events related to failed log in. From **REAL** attackers!
![image](https://github.com/user-attachments/assets/78b2a15e-e55a-44dc-bd4f-81b236002e77)

---

## 🎯 Next Steps
✅ Set up **Log Analytics** to collect event logs.
✅ Integrate with **Microsoft Sentinel** for threat detection.
✅ Use **KQL** queries to analyze attack patterns.

🚀 Proceed to [Log Analytics Setup](log-analytics-setup.md)
