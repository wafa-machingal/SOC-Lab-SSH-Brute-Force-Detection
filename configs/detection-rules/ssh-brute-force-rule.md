# SSH Brute Force Detection Rule

## Overview

This detection rule was created in Kibana Security to identify failed SSH authentication attempts using Linux authentication logs collected through Filebeat.

## Rule Configuration

| Parameter | Configuration |
|---|---|
| Rule Name | SSH Brute Force Attempt Detection |
| Rule Type | Query |
| Index Pattern | `filebeat-*` |
| Query Language | KQL |
| Query | `message: "Failed password"` |
| Severity | Medium |
| Risk Score | 50 |

## Detection Query

```text
message: "Failed password"
```

This query searches for log events containing the phrase "Failed password".

## Observed Results

- Failed SSH authentication events were generated during the lab simulation.
- Filebeat collected and forwarded authentication logs.
- Kibana Discover displayed 33 matching documents in the captured time window.
- The configured detection rule executed successfully.
- Kibana Security displayed generated alerts.

## Security Relevance

Repeated failed SSH authentication attempts may indicate password guessing or brute-force activity.

Monitoring these events helps security analysts identify suspicious authentication activity and investigate potential unauthorized access attempts.

## Evidence

See the screenshots folder for the detection rule configuration, authentication logs and generated security alerts.

## Note

This is a query-based detection rule. It searches for failed password events and should not be confused with a threshold-based aggregation rule.
