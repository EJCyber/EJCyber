# Log Enrichment with Location Data

## Overview
This guide explains how to enrich logs in **Microsoft Sentinel** with **geolocation data** using **Watchlists**. This will help in identifying attack sources based on IP addresses.

## Prerequisites
- **Log Analytics and Microsoft Sentinel** are set up ([Log Forwarding & KQL Queries](log-forwarding-kql.md)).
- A **CSV file** containing geolocation data (e.g., country, city, ISP) for known IPs.

## Steps

### 1️⃣ Create a Watchlist in Sentinel
1. In the **Azure Portal**, go to **Microsoft Sentinel**.
2. Select your **Log Analytics workspace**.
3. Click **Configuration** > **Watchlists**.
4. Click **Create a Watchlist**.
5. Upload a **CSV file** with columns like:
   ```csv
   IP, Country, City, ISP
   192.168.1.1, USA, New York, ISP_A
   203.0.113.5, UK, London, ISP_B
   ```
6. Name the watchlist (e.g., `GeoIP_Watchlist`) and save it.

### 2️⃣ Query Logs with Enriched Data
1. Navigate to **Log Analytics** in **Microsoft Sentinel**.
2. Use **KQL** to join security logs with your watchlist:
   ```kql
   SecurityEvent
   | extend IPAddress = RemoteIP
   | join kind=leftouter Watchlist('GeoIP_Watchlist') on $left.IPAddress == $right.IP
   | project TimeGenerated, IPAddress, Country, City, ISP, EventID, Account
   ```
3. Analyze logs to identify **suspicious geographic patterns**.

## Next Steps
✅ Proceed to **Attack Map Creation** to visualize attack sources.

🚀 Move to [Attack Map Creation](attack-map-creation.md)
