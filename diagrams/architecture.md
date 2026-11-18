
# SOC Lab Architecture

## 1. Project Overview

This document describes the architecture and data flow of a Security Operations Center (SOC) lab built to monitor and investigate SSH authentication failures using the Elastic Stack.

The lab simulates SSH login attempts from Kali Linux against an Ubuntu Linux target. Authentication logs are collected using Filebeat, indexed in Elasticsearch, and monitored through Kibana.

## 2. Lab Environment

| Component | Details |
|---|---|
| Attacker Machine | Kali Linux |
| Target Machine | Ubuntu Linux |
| SIEM Platform | Elastic Stack |
| Log Collection | Filebeat |
| Log Storage and Indexing | Elasticsearch |
| Log Analysis and Visualization | Kibana |
| Attack Protocol | SSH |
| Target IP Address | 192.168.114.130 |
| Observed Source IP | 192.168.114.129 |

## 3. Architecture Diagram

The following diagram represents the logical flow of authentication logs through the SOC environment.

```text
              SOC LAB ARCHITECTURE
              ====================

       +---------------------------+
       |        KALI LINUX         |
       |         ATTACKER          |
       +-------------+-------------+
                     |
                     | SSH Login Attempts
                     v
       +---------------------------+
       |       UBUNTU LINUX        |
       |          TARGET           |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |   AUTHENTICATION LOGS     |
       |         auth.log          |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |         FILEBEAT          |
       |      Log Collection       |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |      ELASTICSEARCH        |
       |       Log Indexing        |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |          KIBANA           |
       |      Log Monitoring       |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |     DETECTION RULE        |
       |   Failed SSH Logins       |
       +-------------+-------------+
                     |
                     v
       +---------------------------+
       |      SECURITY ALERTS      |
       +---------------------------+
```

## 4. Component Description

### Kali Linux - Attacker Machine

Kali Linux was used to simulate SSH authentication attempts against the Ubuntu target machine using an invalid username and password.

### Ubuntu Linux - Target Machine

Ubuntu served as the target system. SSH authentication events were recorded in the Linux authentication logs.

### Filebeat - Log Collection

Filebeat was configured to collect Linux authentication logs and forward them to Elasticsearch for indexing and analysis.

### Elasticsearch - Log Storage and Indexing

Elasticsearch received and indexed the collected authentication events, making them searchable through Kibana.

### Kibana - Monitoring and Analysis

Kibana provided the interface for:
- Searching and investigating authentication logs.
- Filtering failed SSH login events.
- Configuring security detection rules.
- Monitoring generated security alerts.

## 5. Detection Rule Configuration

A custom query-based detection rule was created in Kibana Security to identify failed SSH authentication events.

| Parameter | Configuration |
|---|---|
| Rule Name | SSH Brute Force Attempt Detection |
| Rule Type | Query |
| Index Pattern | filebeat-* |
| Query Language | KQL |
| Severity | Medium |
| Risk Score | 50 |

### Detection Query

```text
message: "Failed password"
```

**Query Language:** Kibana Query Language (KQL)

The query searches indexed log messages for failed password authentication events.

## 6. Data Flow

1. SSH authentication attempts are initiated from Kali Linux against the Ubuntu target.
2. Ubuntu records authentication failures in its authentication logs.
3. Filebeat collects and forwards the log events.
4. Elasticsearch indexes the incoming authentication events.
5. Kibana Discover allows investigation of the collected logs.
6. The configured detection rule searches for matching failed password events.
7. Matching events can generate security alerts in Kibana.

## 7. Observed Results

During the lab exercise, the following results were observed:

- Failed SSH authentication attempts were generated from Kali Linux.
- Authentication failure messages were successfully indexed in Elasticsearch.
- Kibana Discover displayed matching failed password events.
- The custom SSH detection rule was enabled.
- The detection rule successfully executed.
- Security alerts were visible in the Kibana Alerts interface.

## 8. Conclusion

This SOC lab demonstrates the practical implementation of centralized security log collection, monitoring, and detection using the Elastic Stack.

The project provided hands-on experience with Linux authentication logs, SSH security monitoring, Filebeat, Elasticsearch, Kibana, KQL, and SIEM detection rules.

It also demonstrates the basic workflow followed by SOC analysts when investigating suspicious authentication activity.

## 9. Project Scope and Limitations

- The detection query identifies failed password events; it does not independently establish that every matching event is part of a brute-force attack.
- The current rule is a query-based detection rule, not a threshold-based aggregation rule.
- Further improvements could include identifying repeated failures from the same source IP, adding threshold-based detection, and enriching alerts with additional context.


