# Wazuh SIEM Home Lab Setup
Author: Kellie Hucker  

## Overview:
This project provides a high-level overview of my first cybersecurity home lab, built on an HP workstation using VirtualBox. The lab focused on centralized logging, threat detection, and endpoint visibility using Wazuh SIEM. It integrated multiple systems, including Ubuntu-based Wazuh servers and Kali Linux, to simulate a real-world security monitoring environment where logs were collected, forwarded, indexed, and analyzed for security insights.

Beyond deploying a functional SIEM pipeline, this project also involved troubleshooting real-world challenges related to virtual networking, log forwarding, agent communication, and multi-system integration, providing hands-on experience with blue team workflows and security operations concepts.

## Lab Architecture:
<img width="498" height="550" alt="Screenshot 2026-04-16 at 14 07 39" src="https://github.com/user-attachments/assets/e040b115-48f6-4730-b254-57a8fef3fffe" />

### Data Flow:
Endpoint activity on Kali Linux generates system and security logs > Filebeat collects and securely ships logs to the Wazuh server over the network > Wazuh analyzes and enriches events, then indexes them into Elasticsearch > Kibana enables log search, visualization, and alerting for detection and investigation

## Key Actions:
2. Configured VM networking between Ubuntu and Kali Linux
3. Installed and configured Filebeat
4. Forwarded logs from Kali Linux to Wazuh
5. Verified log ingestion into Elasticsearch/Kibana
6. Created test alerts to validate the detection pipeline
7. Integrated additional log sources (Zeek/Suricata)  

## Setup Steps:
*Note: I have detailed documentation on my personal Confluence site*
1. Install Wazuh All-in-One (Ubuntu)
Deployed Wazuh server, including Elasticsearch and Kibana components.
2. Configured VM networking between Ubuntu and Kali Linux
  - Ubuntu (Wazuh server)  
  - Kali Linux (log source)  
3. Install and configure Filebeat on Ubuntu and configure it to forward logs to Wazuh.
4. Confirmed Filebeat logs were being shipped to Elasticsearch/Wazuh.
5. Install Kali Linux VM as a log-generating endpoint.
6. Add Kali as a Log Source and configure log forwarding from Kali Linux to Wazuh using Filebeat.
7. Verified logs from Kali were visible in Wazuh/Kibana.
8. Generated a test event to confirm detection and alerting functionality.
9. Connect Filebeat to Kibana and validate log visualization and dashboard functionality.
10. Add additional log sources (Zeek and Suricata) to expand detection visibility.

Results:
- Successfully built and stabilized my first SIEM home lab  
- Established end-to-end log pipeline from endpoint to SIEM  
- Resolved real-world issues across networking, log shipping, and visibility  
- Gained hands-on experience with troubleshooting and system validation  
- Created a repeatable foundation for future blue team lab expansion

## Issues and Solutions
VM Networking Misconfiguration:
Issue: VirtualBox networking was initially misconfigured, preventing communication between Ubuntu (Wazuh server) and Kali Linux.
- Unable to ping between VMs  
- No logs reaching Wazuh  
- Filebeat appeared functional but no data ingestion  
Solution:
- Reconfigured network adapters using Host-Only + NAT setup  
- Verified IP addressing and subnet alignment  
- Validated connectivity using ping and netstat

Filebeat Not Shipping Logs:
Issue: Filebeat service was running, but logs were not appearing in Wazuh or Elasticsearch.
- Filebeat service active  
- No logs visible in Kibana  
- No indexing activity  
Solution:
- Validated Filebeat configuration file paths  
- Corrected output configuration to point to Wazuh  
- Restarted Filebeat service  
- Confirmed log flow using service logs  

Log Visibility in Kibana:
Issue: Logs were being generated but not visible in dashboards.
- No data in the Discover view  
- Empty dashboards  
Solution:
- Configured correct index patterns in Kibana  
- Verified time range settings  
- Confirmed ingestion using raw index queries  

Kali Linux Log Source Integration
Issue: Kali Linux logs were not initially forwarding correctly.
- No endpoint logs in Wazuh  
- Inconsistent log data  
Solution:
- Configured proper Filebeat inputs on Kali  
- Validated log file paths  
- Ensured network connectivity to the Wazuh server  

General Lab Stability Issues
Issue: Running multiple VMs on a laptop caused performance bottlenecks.
- Slow system performance  
- VM instability during heavy logging  
Solution:
- Tuned VM resource allocation (CPU, RAM)  
- Limited concurrent services  
- Used snapshots to stabilize known-good states

## Security Notes
This project is intended for learning, personal security practice, and portfolio demonstration.
