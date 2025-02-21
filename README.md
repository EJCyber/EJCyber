# Log Analytics Setup Guide

## 📌 Overview
This guide explains how to configure **Azure Log Analytics** to collect, store, and analyze logs from your honeypot VM.

## 🔧 Prerequisites
- **Microsoft Azure account**
- **Honeypot VM deployed** ([Refer to Honeypot Deployment Guide](honeypot-deployment.md))
- **Azure Monitor Permissions**

## 🚀 Configuration Steps

### 1️⃣ Create a Log Analytics Workspace
1. Navigate to **Azure Portal** → **Log Analytics Workspaces**.
2. Click **Create** and configure:
   - **Subscription:** Select your active subscription.
   - **Resource Group:** Use an existing or create a new one.
   - **Region:** Choose a region close to your VM.
   - **Pricing Tier:** Default **Pay-as-you-go** is fine.
3. Click **Review + Create** → **Create**.

### 2️⃣ Connect Your VM to Log Analytics
1. Navigate to **Virtual Machines** → Select your Honeypot VM.
2. Under **Monitoring**, click **Insights** → **Enable**.
3. Select **Log Analytics Workspace** created earlier.
4. Click **Apply** and wait for configuration to complete.

### 3️⃣ Enable Diagnostic Logging
1. Go to **Azure Monitor** → **Diagnostic Settings**.
2. Select **Your Honeypot VM** and click **Add diagnostic setting**.
3. Choose **Send to Log Analytics workspace**.
4. Select relevant log categories (**Security, Audit, Performance**).
5. Click **Save**.

### 4️⃣ Verify Log Collection
1. Navigate to **Azure Log Analytics**.
2. Click **Logs** and run the query:
   ```kql
   SecurityEvent
   | where EventId == 4625
   ```
3. Confirm logs are being ingested.

### 5️⃣ Import GeoIP Data for Enrichment
1. Download **geoip-summarized.csv** (IP Geolocation dataset).
2. Navigate to **Sentinel** → **Watchlists**.
3. Create a new watchlist:
   - **Name/Alias:** geoip
   - **Source Type:** Local File
   - **Search Key:** network
4. Upload `geoip-summarized.csv` and wait for full import (~54,000 rows).
5. Use the following query to enrich security logs with geolocation:
   ```kql
   let GeoIPDB_FULL = _GetWatchlist("geoip");
   let WindowsEvents = SecurityEvent
       | where EventId == 4625
       | evaluate ipv4_lookup(GeoIPDB_FULL, IpAddress, network);
   WindowsEvents
   ```
6. Confirm logs now contain geographic information.

## 🔜 Next Steps
- [Sentinel Integration](sentinel-integration.md)