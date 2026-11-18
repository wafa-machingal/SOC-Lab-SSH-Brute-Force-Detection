# SSH Brute Force Attack Simulation

## 1. Objective

To simulate repeated SSH authentication failures against an Ubuntu target machine using Kali Linux and observe how these events are recorded and detected in the SOC monitoring environment.

## 2. Lab Environment

| Component | Details |
|---|---|
| Attacker | Kali Linux |
| Target | Ubuntu Linux |
| Target IP | `192.168.114.130` |
| Observed source IP | `192.168.114.129` |
| Protocol | SSH |

## 3. Attack Simulation

SSH connection attempts were initiated from Kali Linux against the Ubuntu target using an invalid username.

### Command Used

```bash
ssh fakeuser@192.168.114.130
```

Multiple authentication attempts were made, resulting in failed login responses.

### Observed Terminal Output

The terminal displayed:

- Permission denied messages.
- Repeated password prompts.
- Final authentication failure.

## 4. Log Analysis

The failed SSH authentication events were collected and indexed through Filebeat and Elasticsearch.

In Kibana Discover, the following KQL query was used:

```text
message: "Failed password"
```

The query returned matching failed authentication events.

## 5. Detection Results

The Kibana detection rule identified failed SSH authentication activity.

Observed results included:

- Failed password events in Kibana Discover.
- 33 matching log documents in the captured time window.
- Successful execution of the configured detection rule.
- Security alerts displayed in Kibana.

## 6. Conclusion

This simulation demonstrated how repeated SSH authentication failures can be monitored using centralized log collection and SIEM detection capabilities.

The exercise provided practical experience with SSH security monitoring, Linux authentication logs, KQL searches, and security alert investigation.

## 7. Evidence

Refer to the screenshots folder for the Kali Linux terminal, Kibana authentication logs, detection rule configuration, and generated security alerts.
