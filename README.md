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

## Project Structure

- [docs/architecture.md](docs/architecture.md)
- [docs/lessons_learned.md](docs/lessons_learned.md)
- [screenshots/README.md](screenshots/README.md)

## Screenshots

See the full screenshot index here:

- [screenshots/README.md](screenshots/README.md)

Key evidence included:
- Splunk Enterprise running on Ubuntu
- Receiver port 9997 enabled
- Windows Universal Forwarder installed and configured
- Windows Event Logs successfully ingested into Splunk
- Windows Security logs searchable in Splunk
- Failed logon detection using EventCode 4625
- Scheduled failed logon alert created

## Conclusion

This lab provided a practical foundation for SIEM administration and analyst-style detection work. It demonstrates the full path from Splunk setup to Windows log ingestion, detection validation, and alert creation in a controlled lab environment.
