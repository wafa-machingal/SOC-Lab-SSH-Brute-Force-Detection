# SSH Brute Force Detection using the Elastic Stack

## 1. Project Overview

This project demonstrates the implementation of a Security Operations Center (SOC) lab to detect and monitor SSH brute-force attacks using the Elastic Stack.

The lab simulates SSH authentication attacks from Kali Linux against an Ubuntu system. Authentication logs are collected using Filebeat, processed and indexed in Elasticsearch, and monitored through Kibana.

A threshold-based detection rule identifies repeated failed SSH login attempts and generates alerts for suspicious activity.

## 2. Project Objectives

- Build a functional SOC monitoring environment.
- Collect and analyze Linux authentication logs.
- Simulate SSH brute-force attacks in a controlled lab.
- Identify repeated failed authentication attempts.
- Configure detection rules and generate security alerts.
- Understand the end-to-end security monitoring workflow.

## 3. Lab Architecture

The lab consists of the following components:

| Component | Purpose |
|---|---|
| Kali Linux | Attack simulation |
| Ubuntu Linux | Target system and authentication log source |
| Filebeat | Log collection and forwarding |
| Elasticsearch | Log storage and indexing |
| Kibana | Log visualization, monitoring and alert analysis |

### Architecture Flow

Kali Linux (SSH Attack Simulation)  
↓  
Ubuntu Linux (Authentication Logs)  
↓  
Filebeat (Log Collection)  
↓  
Elasticsearch (Log Storage and Indexing)  
↓  
Kibana (Monitoring and Analysis)  
↓  
Detection Rule and Security Alerts

## 4. Tools & Technologies

- Kali Linux
- Ubuntu Linux
- Elasticsearch
- Kibana
- Filebeat
- SSH
- Linux Authentication Logs

## 5. Implementation

### Step 1: SOC Environment Setup

Set up the Ubuntu environment and configured the Elastic Stack components for centralized log monitoring.

### Step 2: Log Collection

Configured Filebeat to collect Linux authentication logs from the Ubuntu system and forward them to Elasticsearch.

### Step 3: Attack Simulation

Used Kali Linux to simulate SSH brute-force login attempts against the Ubuntu target system in a controlled lab environment.

### Step 4: Log Analysis

Used Kibana to monitor and analyze authentication events, focusing on repeated failed SSH login attempts.

### Step 5: Detection Rule Configuration

Configured a threshold-based detection rule to identify repeated failed SSH authentication attempts.

### Step 6: Alert Generation

Generated and monitored real-time security alerts for suspicious SSH authentication activity through Kibana.

## 6. Detection & Monitoring

The detection process focused on identifying patterns of repeated failed SSH login attempts.

The authentication logs provided visibility into suspicious login activity, while the configured threshold-based rule helped identify potential brute-force behavior.

## 7. Results

The lab successfully demonstrated:

- Centralized collection of Linux authentication logs.
- Visibility into SSH authentication failures.
- Successful simulation of SSH brute-force activity.
- Detection of repeated failed login attempts.
- Generation of security alerts through Kibana.

## 8. Key Learnings

Through this project, I gained practical experience in:

- Configuring and working with the Elastic Stack.
- Linux authentication log analysis.
- Filebeat log collection and forwarding.
- SSH attack simulation in a controlled environment.
- Configuring threshold-based detection rules.
- Monitoring and investigating security alerts.
- Understanding the end-to-end SOC detection workflow.

## 9. Conclusion

This project provided hands-on experience in building a basic SOC monitoring environment and detecting SSH brute-force activity using the Elastic Stack.

It helped strengthen my understanding of security monitoring, log analysis, threat detection, and incident investigation.

---

**Project Category:** Security Operations / SIEM  
**Technologies:** Elasticsearch, Kibana, Filebeat, Kali Linux, Ubuntu Linux
