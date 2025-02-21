# Log Inspection via Event Viewer

## Overview
After setting up the honeypot VM, it's crucial to inspect the logs to detect and analyze attack patterns. This guide explains how to use **Event Viewer** to check security-related events.

## Steps

### 1️⃣ Access Event Viewer
1. Log into your **Honeypot VM** using **Remote Desktop**.
2. Press `Win + R`, type **`Event Viewer`**, and hit **Enter**.
3. In the **Event Viewer**, expand **Windows Logs**, then click **Security**.

### 2️⃣ Filter for Failed Logins
1. In the **Actions** pane, click **Filter Current Log**.
2. In the **Event ID** field, type **4625** (this represents failed login attempts).
3. Click **OK** to filter for these events.

### 3️⃣ Analyze Logs
Review the logs for suspicious patterns, such as multiple failed login attempts from different IPs, which could indicate a brute-force attack.
