# Home SOC Lab – Azure Honeypot & Threat Monitoring

## 🔍 Overview
This project simulates a **Security Operations Center (SOC)** environment by deploying a honeypot in **Microsoft Azure** to monitor and analyze real-world cyber threats. The goal is to enhance **threat detection skills** by collecting, analyzing, and visualizing malicious activities using **Log Analytics, Microsoft Sentinel, and Kusto Query Language (KQL).**

## 🔧 Tools & Technologies Used
- **Microsoft Azure** – Virtual Machine (VM) deployment & cloud security monitoring
- **Microsoft Sentinel** – SIEM for real-time monitoring & threat analysis
- **Log Analytics** – Event data collection & aggregation
- **Kusto Query Language (KQL)** – Custom threat querying & data analysis
- **Attack Mapping** – Visualizing cyber attack patterns

## 🛠 Project Workflow
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

## 🔜 Next Steps & Expansion
- Integrating **Elastic Stack (ELK)** for enhanced log visualization.  
- Implementing **automated alerting** for real-time threat detection.  
- Expanding honeypot capabilities to monitor **different types of cyberattacks**.

## 📂 Repository Structure
```
Home-SOC-Lab/
│── README.md
│── queries/
│   ├── attack-patterns.kql
│   ├── brute-force-detection.kql
│   ├── network-scan-detection.kql
│── screenshots/
│   ├── attack-map.png
│   ├── sentinel-dashboard.png
│── setup/
│   ├── honeypot-deployment.md
│   ├── log-analytics-setup.md
│   ├── sentinel-integration.md
```

## 📜 How to Set Up Your Own SOC Lab
Refer to the setup guides:
- [Honeypot Deployment](setup/honeypot-deployment.md)
- [Log Analytics Setup](setup/log-analytics-setup.md)
- [Sentinel Integration](setup/sentinel-integration.md)

## 🏆 Author
**Emmanuel Johnson** – Entry-Level Cybersecurity Professional
📧 Contact: e.johnson.cyber@gmail.com | 🌐 [LinkedIn Profile](https://www.linkedin.com/in/manny-johnson)

---

🔗 **GitHub Repository:** [Home-SOC-Lab](https://github.com/EJCyber/Home-SOC-Lab)