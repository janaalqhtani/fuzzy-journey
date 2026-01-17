# Enterprise Threat Detection & NCA-ECC Compliance Lab
**Target Role:** Security Operations Center (SOC) Analyst / Security Engineer

## 🎯 Project Overview
This project demonstrates the end-to-end deployment of a **Security Operations Center (SOC)** environment. I have engineered a resilient monitoring system using **Wazuh (SIEM)** and **Sysmon** to detect advanced persistent threats (APTs) and common attack vectors. 

The lab is specifically designed to align with the **National Cybersecurity Authority (NCA) Essential Cybersecurity Controls (ECC)**, simulating the security posture required for a major Saudi industrial entity 
## 🛠️ Core Competencies & Tools
* **SIEM:** Wazuh (Manager, Indexer, Dashboard)
* **Telemetry:** Windows Sysmon (SwiftOnSecurity/MITRE Config)
* **Networking:** VirtualBox Bridged Networking, TCP/IP, Port 1514
* **Compliance:** Saudi NCA-ECC 2024 Framework
* **Security Research:** Threat Hunting, Log Analysis, Attack Simulation
## 🏗️ Technical Architecture

The lab is architected to simulate a corporate DMZ and internal network segment. By utilizing a **Hub-and-Spoke** model, the Wazuh Manager acts as the central intelligence hub, receiving encrypted telemetry from distributed endpoints.

### **Logical Network Map**
```mermaid
graph LR
    subgraph "Internal Network (Victim Zone)"

        WIN["🖥️ Windows 10 Enterprise<br/>(192.168.x.y)"]
        SYSMON["⚙️ Sysmon Service<br/>(MITRE-Mapped)"]
        WIN --- SYSMON
    end

    subgraph "Security Operations Zone (Monitoring)"

        WAZUH["🛡️ Wazuh SIEM Server<br/>(192.168.x.x)"]
        DASH["📊 Web Dashboard<br/>(Port 443)"]
        WAZUH --- DASH
    end

    %% Encrypted Tunnel
    SYSMON -- "Encrypted Logs (Port 1514)" --> WAZUH
## 🛡️ Attack Simulation & Detection Evidence

To verify the effectiveness of the detection engine, I performed a series of controlled attack simulations. These simulations mimic real-world techniques used by adversaries to gain persistence and steal credentials.

### **Test Case 1: Brute Force Attack (Authentication Failure)**
