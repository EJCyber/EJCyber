# Honeypot VM Setup

## Overview
This guide covers creating a **Windows 10 Virtual Machine** in Azure and configuring it as a honeypot to attract and analyze malicious traffic.

## Step 1: Deploy the Virtual Machine
1. Log into [Azure Portal](https://portal.azure.com).
2. Search for **Virtual Machines** in the search bar and select **Create New**.
3. Choose the following settings:
   - **Image:** Windows 10
   - **Size:** Select an appropriate VM size.
   - **Username & Password:** Create a secure login. (Something that you'll remember)
4. Click **Review + Create** and deploy the VM.

## Step 2: Configure the Network Security Group (NSG)
1. Navigate to the **Networking** section of your VM.
2. Locate the **Inbound security rules** and create a new rule:
   - **Source:** Any
   - **Port Range:** Select critical ports to expose (RDP, SSH, HTTP, etc.).
   - **Action:** Allow
3. Apply the changes.

## Step 3: Disable Windows Firewall
1. Log into the newly created VM.
2. Open **Run (Win + R)** and type `wf.msc`, then press **Enter**.
3. In the **Windows Defender Firewall with Advanced Security**, go to **Properties**.
4. Set all profiles (Domain, Private, Public) to **Off**.

## Next Steps
Now that the honeypot is active, proceed to inspecting logs: [Log Inspection](log-inspection.md).
