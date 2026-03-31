# Splunk SIEM Detection Lab

## Overview
This project documents a hands-on Splunk SIEM lab built to ingest Windows Event Logs, verify log visibility in Splunk, detect failed logon activity, and create a scheduled alert for suspicious authentication events.

## Lab Objectives
- Install and configure Splunk Enterprise on Ubuntu
- Enable Splunk boot-start
- Enable Splunk receiving on port 9997
- Install Splunk Universal Forwarder on Windows 11
- Forward Windows Event Logs into Splunk
- Verify Security, System, and Application log ingestion
- Detect failed logon events with EventCode 4625
- Create a scheduled alert for failed logon activity

## Environment
- Host OS: Windows 11
- Guest OS: Ubuntu Desktop (VirtualBox)
- VM Resources: 10 GB RAM, 4 vCPUs, 50 GB disk
- SIEM Platform: Splunk Enterprise
- Forwarder: Splunk Universal Forwarder

## Detection Performed
The main detection used in this lab was:

```spl
index=* sourcetype=WinEventLog:Security EventCode=4625
```
This search was validated by intentionally generating a failed logon attempt on the Windows host and confirming the event appeared in Splunk.

Alert Created

A scheduled alert named Failed Logon Detection was created in Splunk using the failed logon search. The alert was configured to trigger when the number of results was greater than zero and to add matching events to Triggered Alerts.

Project Structure
docs/architecture.md
docs/lessons_learned.md
screenshots/
Screenshots
01-splunk-web-ui-running.png
02-splunk-boot-start-enabled.png
03-splunk-receiver-port-9997-enabled.png
04-ubuntu-vm-nat-ip-address.png
05-virtualbox-nat-port-forwarding-9997.png
06-windows-localhost-port-9997-test-success.png
07-splunk-universal-forwarder-installed.png
08-uf-outputs-conf-configured.png
09-uf-inputs-conf-wineventlog-enabled.png
10-splunk-forwarder-service-restarted.png
11-windows-event-logs-ingested-in-splunk.png
12-windows-security-logs-in-splunk.png
13-failed-logon-event-4625-detected.png
14-failed-logon-alert-created.png
Conclusion

This lab provided a practical foundation for SIEM administration and analyst-style detection work. It demonstrates the full path from Splunk setup to Windows log ingestion, detection validation, and alert creation in a controlled lab environment.
