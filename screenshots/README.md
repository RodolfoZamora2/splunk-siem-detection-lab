# Screenshots

## Splunk SIEM Detection Lab Evidence

1. **01-splunk-web-ui-running.png** - Splunk Enterprise running on the Ubuntu VM.
2. **02-splunk-boot-start-enabled.png** - Splunk configured to start automatically at boot.
3. **03-splunk-receiver-port-9997-enabled.png** - Splunk listening on TCP port 9997 for forwarded data.
4. **04-ubuntu-vm-ip-address.png** - Ubuntu VM IP address used for lab validation.
5. **05-virtualbox-nat-port-forwarding-9997.png** - VirtualBox NAT rule forwarding host port 9997 to the Ubuntu VM.
6. **06-windows-localhost-port-9997-test-success.png** - Windows host successfully connecting to localhost port 9997.
7. **07-splunk-universal-forwarder-installed.png** - Splunk Universal Forwarder installed and running on Windows 11.
8. **08-uf-outputs-conf-configured.png** - Universal Forwarder outputs.conf configured to forward logs to Splunk.
9. **09-uf-inputs-conf-wineventlog-enabled.png** - Universal Forwarder inputs.conf configured to collect Windows Event Logs.
10. **10-splunk-forwarder-service-restarted.png** - Splunk Forwarder service verified running after configuration.
11. **11-windows-event-logs-ingested-in-splunk.png** - Windows Event Logs successfully ingested into Splunk.
12. **12-windows-security-logs-in-splunk.png** - Windows Security logs visible in Splunk search results.
13. **13-failed-logon-event-4625-detected.png** - Failed Windows logon events detected using EventCode 4625.
14. **14-failed-logon-alert-created.png** - Scheduled Splunk alert created for failed logon detection.
