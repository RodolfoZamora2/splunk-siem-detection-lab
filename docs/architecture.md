# Architecture

## Lab Purpose
The purpose of this lab was to build a basic Splunk SIEM pipeline capable of receiving Windows Event Logs, indexing them, searching them, and generating an alert for failed logon activity.

## Components

### Windows 11 Host
The Windows host acted as the log source and ran Splunk Universal Forwarder.

### Ubuntu Virtual Machine
The Ubuntu VM hosted Splunk Enterprise and served as the SIEM platform for receiving, indexing, searching, and alerting on logs.

### Splunk Enterprise
Splunk Enterprise was installed on Ubuntu and configured to:
- start at boot
- listen on TCP 9997
- provide a web interface on port 8000

### Splunk Universal Forwarder
Splunk Universal Forwarder was installed on Windows 11 and configured to:
- collect Windows Event Logs
- send those logs to Splunk over TCP 9997

### VirtualBox NAT Port Forwarding
VirtualBox NAT port forwarding allowed the Windows host to send traffic to the Ubuntu guest.

## Data Flow
1. A Windows event is generated on the host machine.
2. Splunk Universal Forwarder reads the event from Windows Event Logs.
3. Universal Forwarder sends the event to `127.0.0.1:9997`.
4. VirtualBox NAT forwarding redirects that traffic to the Ubuntu guest.
5. Splunk Enterprise receives the event on TCP 9997.
6. Splunk indexes the event.
7. Searches and alerts can be run against the ingested data.

## Detection Flow
The main validation detection in this lab was:

```spl
index=* sourcetype=WinEventLog:Security EventCode=4625
```
This search was validated by intentionally generating failed logon attempts on the Windows host and confirming the events appeared in Splunk.

Diagram

Windows 11 Host
 ├─ Security / System / Application Logs
 └─ Splunk Universal Forwarder
        |
        | sends to 127.0.0.1:9997
        v
VirtualBox NAT Port Forwarding
        |
        v
Ubuntu VM
 └─ Splunk Enterprise
      ├─ receives logs
      ├─ indexes logs
      ├─ searches logs
      └─ triggers alerts
      
