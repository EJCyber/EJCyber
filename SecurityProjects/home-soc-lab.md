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

## 📌 Key Findings
✅ Identified multiple brute-force login attempts and network scanning activities.  
✅ Detected suspicious IPs and their geographical locations.  
✅ Analyzed attacker dwell time and attack vectors.  

Through this lab, I identified real-world attack trends, strengthening my threat detection and analysis skills.

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
- [Azure Subscription Setup](setup/azure-subscription-setup.md)
- [Honeypot VM Setup](setup/honeypot-vm-setup.md)
- [Log Inspection](setup/log-inspection.md)
- [Log Forwarding, Log Analytics, and KQL Queries](SecurityProjects/setup/log-forward-kql.md)
- [Log Enrichment & Location Data](setup/log-enrichment-location-data.md)
- [Attack Map Creation](setup/attack-map-creation.md)

## 🏆 Author
**Emmanuel Johnson** – Aspiring SOC Analyst | Cybersecurity Enthusiast  
📧 Contact: e.johnson.cyber@gmail.com | 🌐 [LinkedIn Profile](https://www.linkedin.com/in/manny-johnson)

---

🔗 **GitHub Repository:** [Home-SOC-Lab](https://github.com/EJCyber/Home-SOC-Lab)
