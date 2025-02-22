# Log Forwarding, Log Analytics, and KQL Queries

## Overview
This guide explains how to set up **Log Analytics** to collect logs from your honeypot VM and integrate them with **Microsoft Sentinel**. You'll also learn how to analyze logs using **Kusto Query Language (KQL)**.

## Prerequisites
- **Azure Log Analytics** workspace created.
- **Microsoft Sentinel** integration for advanced threat detection.

---

## Steps

### 1️⃣ Set Up Log Analytics Workspace
1. In the **Azure Portal**, search for **Log Analytics Workspaces**.
2. Click **Create** and fill in the details:
   - **Subscription**: Select your active subscription.
   - **Resource Group**: Select `RG-SOC-Lab`.
   - **Workspace Name**: `LAW-soc-Lab` (or choose any name).
   - **Region**: `East US 2`.
3. Click **Review + Create**, then **Create**.

---

### 2️⃣ Set Up Microsoft Sentinel
1. In the **Azure Portal**, search for **Microsoft Sentinel**.
2. Click **Create** (you should see the Log Analytics workspace you just created).
3. Click on **Log Analytics workspace** to link it to **Microsoft Sentinel** so we can access our log repository from the SIEM.

---

### 3️⃣ Connect Log Analytics Workspace to Virtual Machine via Sentinel
> **Keep in mind** you will see a pop-up that mentions the **Sentinel trial** has been activated. This trial lasts for 30 days, and if you continue to run your VM, charges may be incurred.

1. Once the connection between **Sentinel** and the **Log Analytics workspace** is confirmed, we need to configure the **Azure Monitoring Agent (AMA)** connector. This creates the connection between our virtual machines and our Log Analytics workspace in Sentinel.
2. In **Microsoft Sentinel**, click on the connected **Log Analytics Workspace**.
3. Click on the **Content Management** drop-down, then select **Content Hub**.
4. In the search bar, type **Security Event**.
5. Select **Windows Security Event**, then click **Install**.
6. After installation, click on **Windows Security Event** again, then click **Manage**.
7. Select **Windows Security Events via AMA**.
8. Click the **Open Connector Page** button (this is where we will begin to configure a data collection rule).
9. Type in a name (e.g., `DCR-Windows`).
10. Choose the active **Subscription** and the **Resource Group** we created earlier, then click **Next**.
11. Expand the **Azure subscription** drop-down, then expand the **Resource Group** drop-down, and select the **Virtual Machine**. Click **Next**.
12. Leave the **All Security Event** option checked, then click **Next** and select **Create**.

---

### 4️⃣ Verify Installation of AMA Extension
1. After receiving a **Successfully installed extension** alert, open a new tab and navigate back to your VM in **Azure**.
2. Select **Settings**, then **Extensions & Apps**. Here you should be able to view the **AMA extension**.
3. The status may show as **Unavailable** initially, meaning no data is being forwarded yet. This may take some time.
4. Once the status of the extension changes to **Installed**, that is when logs will begin to be forwarded to your **Log Analytics Workspace**. (The timing for when logs start appearing in the Log Analytics Workspace depends on the amount of traffic the honeypot VM receives. The more activity or potential attacks the VM attracts, the sooner you will see logs in the workspace.)

---

### 5️⃣ Run Kusto Query Language (KQL) Queries
1. In **Log Analytics**, go to **Logs**.
2. Use **KQL** to run queries and identify attack patterns such as:
   - **Failed logins**:
     ```kql
     SecurityEvent
     | where EventID == 4625
     ```
   - **Suspicious account lockouts**:
     ```kql
     SecurityEvent
     | where EventID == 4740
     ```

---

## 🎯 Next Steps
- After forwarding logs to **Microsoft Sentinel**, proceed with **Log Enrichment** in [Log Enrichment & Location Data](setup/log-enrichment-location-data.md)
- Use **KQL queries** for deeper analysis and visualization as outlined in the [Attack Map Creation](setup/Attack-Map-Creation-in-Microsoft-Sentinel.md).
