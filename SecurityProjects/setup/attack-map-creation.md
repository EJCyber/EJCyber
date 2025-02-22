# Attack Map Creation in Microsoft Sentinel

## Overview
This guide explains how to create an **Attack Map** in **Microsoft Sentinel** using workbooks to visualize attack patterns based on geo-location data.

## Prerequisites
- **Log Analytics and Sentinel Setup Completed** [Log Forwarding & KQL Queries](log-forward-kql.md)
- **Geo-location data enrichment implemented** [Log Enrichment with Location Data](log-enrichment-location-data.md)

## Steps

## 1️⃣ Open Microsoft Sentinel Workbooks
1. Navigate to **Microsoft Sentinel** in the **Azure Portal**.
2. Select your **Log Analytics Workspace**.
3. Under **Threat Management**, click **Workbooks**.
4. Click **+ New** to create a new workbook.

## 2️⃣ Add a Query-Based Visualization
1.Click **Edit**, then Click the **...** on the right side to remove the default visuals.
![image](https://github.com/user-attachments/assets/b6fa1527-8a4c-4103-a7f8-51d586f9331d)
2. Click **Add**, then **Add Query**![image](https://github.com/user-attachments/assets/5ab0c733-20bd-46fe-bb0e-cf9f02cd6c74)

3. Select **Log Analytics** as the data source.
4. Use the following **KQL Query** to retrieve attack locations:

   ```kql
   SecurityEvent
   | where EventID == 4625  // Failed login attempts
   | extend AttackerIP = IpAddress
   | lookup GeoLocation on AttackerIP
   | project TimeGenerated, AttackerIP, Country, Latitude, Longitude
   ```

4. Click **Run** to preview the data.
5. Click **Visualization** and select **Map**.

## 3️⃣ Customize the Attack Map
1. Set **Latitude** and **Longitude** as location fields.
2. Use **Country** as the display label.
3. Adjust visualization settings to enhance readability.
![Screenshot_20250222_161823_Chrome](https://github.com/user-attachments/assets/5002cc87-2b33-4c1e-886e-7c1f4e905df4)


## 4️⃣ Save and Deploy
1. Click **Save** and enter a meaningful name like `Attack Map Workbook`.
2. Click **Done Editing**.
3. The attack map should now display failed login attempts and their locations.
![Screenshot_20250222_150246_Chrome](https://github.com/user-attachments/assets/a007e01c-ca0c-4c02-a70c-cae4a17d66e5)

## Next Steps
✅ Enhance visualization with additional filters (e.g., specific time ranges).
✅ Set up alerts based on unusual geo-location patterns.
✅ Review attack trends regularly in **Microsoft Sentinel**.

🚀 You have now successfully built a **real-time attack map** in **Microsoft Sentinel**!
