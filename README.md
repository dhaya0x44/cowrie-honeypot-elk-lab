# 🛡️ Cowrie Honeypot + ELK Stack Detection Lab

## 🔍 Overview
This project demonstrates the design, deployment, and monitoring of a real-world SSH honeypot using **Cowrie**, integrated with the **ELK Stack (Elasticsearch, Filebeat, Kibana)** for log ingestion and detection.

The objective is to simulate attacker behavior, capture malicious activity, and build visibility through centralized logging and analysis — mimicking real SOC and detection engineering workflows.

---

## ⚙️ Architecture

Kali Linux (Attacker)  
        ↓  
Cowrie Honeypot (Raspberry Pi)  
        ↓  
Filebeat (Log Shipper)  
        ↓  
Elasticsearch (Storage & Indexing)  
        ↓  
Kibana (Visualization & Analysis)

---

## 🧪 Attack Scenarios

### 1. SSH Brute Force Attack (Hydra)
- Simulated credential brute force using Hydra from Kali Linux
- Multiple login attempts with username/password combinations
- Captured:
  - Failed login attempts
  - Successful authentication events

---

### 2. Interactive Command Execution
- Attacker gained access to the honeypot via SSH
- Executed common reconnaissance commands:
  - `whoami`
  - `pwd`
  - `uname -a`
  - `cat /etc/passwd`
- Captured full attacker session activity

---

### 3. Post-Exploitation Behavior Simulation
- Simulated attacker exploring the environment after login
- Observed command patterns and interaction flow
- Logged attacker intent and behavior for analysis

---

## 📊 Detection & Log Analysis (Kibana)

Logs were ingested into Elasticsearch using Filebeat and visualized in Kibana.

### Key Detections

- **Brute Force Activity**
  - Multiple login attempts detected from single IP
  - Identified via repeated authentication events

- **Successful Login Detection**
  - Detection of valid credential usage
  - Logged username and password combinations

- **Command Execution Monitoring**
  - Tracking attacker commands via:
    ```
    eventid: "cowrie.command.input"
    ```

---

## 🔎 Sample KQL Queries

```
eventid: "cowrie.login.failed"

eventid: "cowrie.login.success"

eventid: "cowrie.command.input"
```

---

## 📈 Results

- Successfully captured and analyzed attacker behavior in real time
- Built visibility into:
  - Authentication attacks
  - Session activity
  - Command execution patterns
- Demonstrated practical detection engineering workflow using ELK Stack

---

## 🛠️ Technologies Used

- Cowrie Honeypot
- Elasticsearch
- Filebeat
- Kibana
- Kali Linux
- Hydra

---

## 🛡️ Key Learnings

- Practical implementation of honeypots for threat detection  
- Log pipeline creation using Filebeat → Elasticsearch  
- Writing detection logic using Kibana Query Language (KQL)  
- Understanding attacker behavior during SSH-based intrusions  
- Hands-on experience in SOC-style monitoring and analysis  

---

## 🚀 Future Improvements

- Integration with alerting (ElastAlert / SIEM rules)
- Dashboard creation for attack visualization
- GeoIP enrichment for attacker source tracking
- Automated detection rules for brute-force patterns

---

## 📸 Screenshots

- Hydra brute force execution (Kali)
![Hydra Attack](screenshots/screenshots-attack-hydra.png)
  
- Cowrie logs capturing login attempts
![Cowrie Logs](screenshots/screenshots-cowrie-logs.png)
  
- Kibana Discover view with login events
![Kibana Login](screenshots/screenshots-kibana-login.png)
  
- Command execution logs (`whoami`, `uname -a`)
![Command Execution](screenshots/screenshots-command-execution.png)
 
- Attacker Command Activity (Kibana)
![Kibana Commands](screenshots/screenshots-kibana-commands.png)

---

## 📌 Conclusion

This project showcases hands-on skills in detection engineering, log analysis, and adversary simulation.  
It reflects real-world SOC operations and demonstrates the ability to detect, analyze, and interpret attacker behavior using industry-standard tools.

