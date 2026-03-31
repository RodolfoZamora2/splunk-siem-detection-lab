# Lessons Learned

## 1. SIEM setup is more than installing Splunk
Installing Splunk was only the first step. The lab also required enabling boot-start, enabling receiving on port 9997, and validating that the service was listening.

## 2. Connectivity testing matters before ingestion testing
Before focusing on Splunk searches, it was necessary to verify:
- Splunk was running
- port 9997 was listening
- Windows could reach the listener

## 3. Virtual networking can become a major troubleshooting point
The original host-only networking approach caused problems, which led to using NAT port forwarding instead. This reinforced how often lab issues come from networking rather than the security tool itself.

## 4. Log collection requires both outputs and inputs
Universal Forwarder needed:
- `outputs.conf` to define where logs go
- `inputs.conf` to define which logs are collected

Both were necessary for successful forwarding.

## 5. Validation works best in layers
This lab was easiest to complete by validating one step at a time:
1. Splunk web access
2. boot-start
3. receiver port
4. connectivity
5. forwarder install
6. forwarder config
7. restart
8. ingestion verification
9. detection validation
10. alert creation

## 6. Detection logic needs precision
Searching only for `EventCode=4625` was not enough by itself. Narrowing the query to:

```spl
index=* sourcetype=WinEventLog:Security EventCode=4625
```
made the detection more accurate and relevant.

7. Documentation makes the project stronger

Capturing screenshots at each milestone created proof for setup, ingestion, detection, and alerting, which makes the project stronger both for learning and for GitHub presentation.

Final Takeaway

This project showed how to build, test, troubleshoot, and document a basic SIEM workflow end to end in a home lab environment.
