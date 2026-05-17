# Blue Team Home Lab:
Author: Kellie Hucker  

## Overview
This project documents the setup of a home cybersecurity lab focused on centralized logging, detection, and visibility using Wazuh SIEM. The lab integrates multiple systems, including Ubuntu (Wazuh server) and Kali Linux, to simulate a real-world environment where logs are collected, forwarded, and analyzed for security insights. This was my first home cybersecurity lab, built on an HP laptop using VirtualBox. The project focused not only on standing up a working SIEM pipeline, but also on troubleshooting real-world issues related to networking, log forwarding, and system integration.

## Objective
- Build a functional SIEM lab environment  
- Centralize logs using Wazuh  
- Forward logs from multiple systems  
- Validate log ingestion and visibility  
- Simulate detection and alert generation  

## Lab Architecture
<img width="498" height="550" alt="Screenshot 2026-04-16 at 14 07 39" src="https://github.com/user-attachments/assets/e040b115-48f6-4730-b254-57a8fef3fffe" />
    
### Data Flow
- Endpoint activity on Kali Linux generates system and security logs  
- Filebeat collects and securely ships logs to the Wazuh server over the network  
- Wazuh analyzes and enriches events, then indexes them into Elasticsearch  
- Kibana enables log search, visualization, and alerting for detection and investigation  

## Key Actions Taken
- Installed Wazuh All-in-One on Ubuntu  
- Configured VM networking between Ubuntu and Kali Linux  
- Installed and configured Filebeat  
- Forwarded logs from Kali Linux to Wazuh  
- Verified log ingestion into Elasticsearch/Kibana  
- Created test alerts to validate the detection pipeline  
- Integrated additional log sources (Zeek/Suricata)  

## Key Steps (Technical Summary)
### 1. Install Wazuh All-in-One (Ubuntu)
Deployed Wazuh server, including Elasticsearch and Kibana components.

### 2. Configure VM Networking
Configured VirtualBox networking to allow communication between:
- Ubuntu (Wazuh server)  
- Kali Linux (log source)  

### 3. Install and Configure Filebeat
Installed Filebeat on Ubuntu and configured it to forward logs to Wazuh.

### 4. Verify Filebeat Log Shipping
Confirmed logs were being shipped to Elasticsearch/Wazuh.

### 5. Install Kali Linux (VirtualBox)
Deployed Kali Linux VM as a log-generating endpoint.

### 6. Add Kali as a Log Source
Configured log forwarding from Kali Linux to Wazuh using Filebeat.

### 7. Validate Log Ingestion
Verified logs from Kali were visible in Wazuh/Kibana.

### 8. Create Test Alert
Generated a test event to confirm detection and alerting functionality.

### 9. Connect Filebeat to Kibana
Validated log visualization and dashboard functionality.

### 10. Add Additional Log Sources
Integrated Zeek and Suricata logs to expand detection visibility.

## Outcome
- Successfully built and stabilized my first SIEM home lab  
- Established end-to-end log pipeline from endpoint to SIEM  
- Resolved real-world issues across networking, log shipping, and visibility  
- Gained hands-on experience with troubleshooting and system validation  
- Created a repeatable foundation for future blue team lab expansion

## Lab Evolution
This project was initially built on an HP laptop as my first home lab environment.
- As the lab matured, I migrated the blue team infrastructure to a dedicated Acer system to improve performance and maintain a stable monitoring environment.
- The HP laptop is now being repurposed to simulate red team activity, enabling a controlled setup where mock enterprise attacks can be generated and observed within the lab.
- This separation allows for more realistic testing of detection pipelines and blue team workflows.

## Issues and Solutions
### 1. VM Networking Misconfiguration
#### Issue: VirtualBox networking was initially misconfigured, preventing communication between Ubuntu (Wazuh server) and Kali Linux.

#### Symptoms:
- Unable to ping between VMs  
- No logs reaching Wazuh  
- Filebeat appeared functional but no data ingestion  

#### Solution:
- Reconfigured network adapters using Host-Only + NAT setup  
- Verified IP addressing and subnet alignment  
- Validated connectivity using ping and netstat

### 2. Filebeat Not Shipping Logs
#### Issue: Filebeat service was running, but logs were not appearing in Wazuh or Elasticsearch.

#### Symptoms:
- Filebeat service active  
- No logs visible in Kibana  
- No indexing activity  

#### Solution:
- Validated Filebeat configuration file paths  
- Corrected output configuration to point to Wazuh  
- Restarted Filebeat service  
- Confirmed log flow using service logs  

### 3. Log Visibility in Kibana
#### Issue: Logs were being generated but not visible in dashboards.

#### Symptoms:
- No data in the Discover view  
- Empty dashboards  

#### Solution:
- Configured correct index patterns in Kibana  
- Verified time range settings  
- Confirmed ingestion using raw index queries  

### 4. Kali Linux Log Source Integration
#### Issue: Kali Linux logs were not initially forwarding correctly.

#### Symptoms:
- No endpoint logs in Wazuh  
- Inconsistent log data  

#### Solution:
- Configured proper Filebeat inputs on Kali  
- Validated log file paths  
- Ensured network connectivity to the Wazuh server  

### 5. General Lab Stability Issues
#### Issue: Running multiple VMs on a laptop caused performance bottlenecks.

#### Symptoms:
- Slow system performance  
- VM instability during heavy logging  

#### Solution:
- Tuned VM resource allocation (CPU, RAM)  
- Limited concurrent services  
- Used snapshots to stabilize known-good states

## Security Notes
This project is intended for learning, personal security practice, and portfolio demonstration.

