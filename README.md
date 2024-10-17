# Active-Directory-Project

# Network Setup Documentation: Cyberworkx Domain

## Overview

This network setup represents a small lab environment, designed for monitoring and identifying potential cyberattacks using Splunk and Sysmon. The setup includes a Windows 10 machine, Active Directory, a Splunk server, and an attacking machine (Kali Linux). The purpose of this lab is to collect and analyze logs for suspicious activities, especially on the Active Directory server and the Windows 10 machine, using Splunk

![Active Directory Project drawio](https://github.com/user-attachments/assets/d6d7169a-d425-45eb-af68-f0ed3daf34af)

## Network Information
- **Domain Name**: Cyberworkx
- **IP Address Range**: 192.168.10.0/24

## Devices in the Network
- **Splunk Server**
  - **IP**: 192.168.10.10
  - **Purpose**: Centralized logging and monitoring server.
  - **Function**: Receives logs from Active Directory and Windows 10 machines using the Splunk Universal Forwarder and performs analysis to detect any suspicious activity.
    
- **Active Directory Server**
  - **IP**: 192.168.10.7
  - **Role**: Manages domain services like user authentication and group policies for the Cyberworkx domain.
  - **Log Forwarding**: Sysmon and Splunk Universal Forwarder are installed to capture detailed system logs and forward them to the Splunk server.
    
- **Windows 10 Machine**
  - **IP**: Dynamically assigned via DHCP
  - **Role**: A client machine in the Cyberworkx domain.
  - **Log Forwarding**: Like the Active Directory server, Sysmon is installed along with Splunk Universal Forwarder to collect system events and forward them to the Splunk server for analysis.
    
- **Kali Linux (Attacker)**
  - **IP**: 192.168.10.250
  - **Role**: An external attacking machine used for penetration testing and simulating cyberattacks. This machine will attempt attacks on the Active Directory or Windows 10 machine to test the monitoring and detection capabilities of the network.


## Device Configuration
1. ### Splunk Server
 - **IP Address**: 192.168.10.10
 - **Software Installed:**
   - **Splunk Enterprise**: Collects and analyzes machine-generated data.
   - **Data Forwarding**: Receives logs from the Active Directory and Windows 10 machines via the Splunk Universal Forwarder.
   - **Monitoring**: Dashboard and alerts are set up to notify when suspicious activities are detected.
     
2. ### Active Directory Server
  - **IP Address**: 192.168.10.7
  - **Role**: Central domain controller for Cyberworkx.
  - **Software Installed:**
    - **Active Directory Domain Services**: Manages domain resources and users.
    - **Sysmon**: Monitors and logs system events.
    - **Splunk Universal Forwarder**: Forwards logs from Sysmon to the Splunk server.
      
3. ### Windows 10 Client
  - **IP Address**: DHCP assigned.
  - **Software Installed:**
    - **Sysmon**: Used to capture detailed logs of system events. 
    - **Splunk Universal Forwarder**: Forwards system logs to Splunk for centralized monitoring.
      
4. ### Kali Linux (Attacker)
  - **IP Address**: 192.168.10.250
  - **Role**: A machine for simulating attacks on the Windows 10 machine and Active Directory server.
  - **Software Installed:**
    - Standard Kali Linux tools for penetration testing (e.g., nmap, Metasploit, etc.).

## Communication Flow
1. ### Log Forwarding:
  - Both the Windows 10 and Active Directory servers use Sysmon to log important system activities such as process creation, network connections, and changes to file integrity.
  - These logs are forwarded using the Splunk Universal Forwarder to the Splunk server for centralized analysis.

2. ### Attack Simulation:
 - The Kali Linux machine simulates cyberattacks (e.g., brute force, network scanning) on both the Windows 10 machine and the Active Directory server.
 - Logs generated as a result of these activities are captured by Sysmon on the Windows 10 and Active Directory servers, then forwarded to Splunk for analysis.

3. ### Log Analysis:
  - The Splunk server analyzes the forwarded logs, looking for signs of suspicious activities like failed login attempts, unusual network connections, or privilege escalations.
  - Alerts and dashboards on Splunk help in identifying any suspicious behavior in real time.


## Key Monitoring Tools
  - **Sysmon (System Monitor):**
    - Installed on both the Active Directory server and Windows 10 machine.
    - Captures detailed information about system processes, network connections, and file changes, aiding in security event analysis.

  - **Splunk Universal Forwarder:**
    - Installed on both the Active Directory server and Windows 10 machine.
    - Forwards all Sysmon-generated logs to the Splunk server for centralized storage and analysis.


## Potential Use Cases
  - **Security Incident Detection**: This setup is designed to monitor critical events such as privilege escalation, process creation, and network connections to detect potential threats to the network.
  - **Threat Hunting**: The Kali Linux machine can be used to simulate attacks, which can help in verifying the effectiveness of the log collection and monitoring setup using Splunk and Sysmon.
  - **Log Forensics**: Investigating suspicious events by correlating logs across the Windows 10 and Active Directory systems.


## Summary
This network diagram only represents a small-scale security lab I have designed to simulate cyberattacks using the Kali Linux machine, with centralized log monitoring and analysis provided by a Splunk server. The integration of Sysmon and the Splunk Universal Forwarder allows for detailed event logging and monitoring, especially for system events on the Windows 10 and Active Directory machines.

The primary goal is to detect and respond to suspicious activities in the Cyberworkx domain and provide insights into potential security breaches through advanced logging and monitoring.
