Day 1 – Terminal Session Log

This log records the exact terminal commands and observations from the first full work session on the Raspberry Pi 5 while building the Pi-hole ad-blocker system.

1. Connecting to the Raspberry Pi

Connected over SSH from a Mac terminal using the hostname created in Raspberry Pi Imager:
````
ssh black_pearl_captain@10.0.0.39
````
Confirmed the Pi was reachable: 
````
ping 10.0.0.39
````
2. Checking System State

Verified the Pi booted correctly and was connected to Wi-Fi:
````
ip a
````
Checked running processes and general system health: 
````
uptime
````
````
df -h
````
3. Running Updates

Updated package lists and installed the latest patches:
````
sudo apt update
````
````
sudo apt upgrade -y
````
These updates ensured secure and current software before installing Pi-hole.

4. Installing and Testing Pi-hole

Launched the Pi-hole installer:
````
curl -sSL https://install.pi-hole.net | bash
````
After installation, verified service health:
````
pihole status
````
Checked DNS queries on the dashboard and inspected log activity.

5. Testing DNS Resolution

Verified DNS queries were resolving through Pi-hole:
````
nslookup google.com
````
Tested IPv4 connectivity:
````
ping 1.1.1.1
````
6. Reviewing Logs

Checked Pi-hole’s FTL logs for real-time DNS activity:
````
sudo tail -f /var/log/pihole-FTL.log
````
Confirming the service was receiving and filtering DNS queries.

---

Summary

At the end of Day 1:
	•	SSH access was working
	•	System updates were complete
	•	Pi-hole was installed and running
	•	DNS queries resolved through Pi-hole
	•	Logs confirmed active packet filtering
	•	Raspberry Pi was ready for static IP configuration and further testing
