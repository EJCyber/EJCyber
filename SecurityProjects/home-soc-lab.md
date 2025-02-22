# Home SOC Lab – Azure Honeypot & Threat Monitoring

## 🔍 Overview
This project simulates a **Security Operations Center (SOC)** environment by deploying a honeypot in **Microsoft Azure** to monitor and analyze real-world cyber threats. The goal is to enhance **threat detection skills** by collecting, analyzing, and visualizing malicious activities using **Log Analytics, Microsoft Sentinel, and Kusto Query Language (KQL).**

## 🔧 Tools & Technologies Used
- **Microsoft Azure** – Virtual Machine (VM) deployment & cloud security monitoring
- **Microsoft Sentinel** – SIEM for real-time monitoring & threat analysis
- **Log Analytics** – Event data collection & aggregation
- **Kusto Query Language (KQL)** – Custom threat querying & data analysis
- **Attack Mapping** – Mapping & analyzing attack patterns to understand adversary tactics

## 🛠 Project Workflow
This lab follows a structured approach to deploy a honeypot, collect security logs, analyze threats, and map attack behaviors.

### 1️⃣ Deploying the Honeypot
- Created a **Windows/Linux VM** in Azure and exposed select services to attract malicious traffic.
- Configured firewall and network settings to simulate a vulnerable system.

### 2️⃣ Log Collection & Aggregation
- Captured incoming attacks and logged activity via **Azure Log Analytics**.
- Forwarded logs to **Microsoft Sentinel** for centralized monitoring.

### 3️⃣ Threat Analysis Using KQL
- Queried **Log Analytics Workspace** to extract attack patterns.
- Filtered and visualized attack sources, methods, and timestamps.

### 4️⃣ Building an Attack Map
- Mapped out attack patterns to understand adversary behavior.
- Documented findings and security recommendations.

## 🔍 Findings & Analysis  
One of the key insights from this project was visualizing global attack sources.  
The image below illustrates real-time attack data collected from the honeypot VM.

### **Windows VM Attack Heat Map**
[Windows VM Attack Map] >Screenshot_20250222_150246_Chrome.jpg<

**Key Observations:**
- **High attack activity** from regions like **South Korea, Middle East, and North America**.
- Multiple **brute-force login attempts** detected.
- Evidence of **port scanning** from distributed IP addresses.
- Used **KQL queries** to filter, analyze, and respond to threats effectively.

## 🔜 Next Steps & Expansion
- Integrating **Elastic Stack (ELK)** for enhanced log visualization.  
- Implementing **automated alerting** for real-time threat detection.  
- Expanding honeypot capabilities to monitor **different types of cyberattacks**.  

I am currently testing ELK integration and plan to implement automated alerting soon.

## 📂 Repository Structure
```yaml
Home-SOC-Lab/
├── README.md
├── queries/
│   ├── attack-patterns.kql
│   ├── brute-force-detection.kql
│   ├── network-scan-detection.kql
├── screenshots/
│   ├── attack-map.png
│   ├── sentinel-dashboard.png
├── setup/
│   ├── honeypot-deployment.md
│   ├── log-analytics-setup.md
│   ├── sentinel-integration.md
│   ├── azure-subscription-setup.md
│   ├── honeypot-vm-setup.md
│   ├── log-inspection.md
│   ├── log-forwarding-kql.md
│   ├── log-enrichment-location-data.md
│   ├── attack-map-creation.md
```

## 📜 How to Set Up Your Own SOC Lab
Refer to the setup guides:
- [Setting Up an Azure Subscription](setup/azure-subscription-setup.md)
- [Honeypot VM Setup in Azure](setup/honeypot-vm-setup.md)
- [Log Inspection via Event Viewer](setup/log-inspection.md)
- [Log Forwarding, Log Analytics, and KQL Queries](setup/log-forward-kql.md)
- [Log Enrichment & Location Data](setup/log-enrichment-location-data.md)
- [Attack Map Creation in Microsoft Sentinel](setup/attack-map-creation.md)

## 🏆 Author
**Emmanuel Johnson** – Aspiring SOC Analyst | Cybersecurity Enthusiast  
📧 Contact: e.johnson.cyber@gmail.com | 🌐 [LinkedIn Profile](https://www.linkedin.com/in/manny-johnson)

---

🔗 **GitHub Repository:** [Home-SOC-Lab](https://github.com/EJCyber/Home-SOC-Lab)
