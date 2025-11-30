02 – Pi-hole Configuration

This document explains how Pi-hole was configured after installation, including password setup, service verification, and initial dashboard access.

⸻

1. Setting the Admin Password

The first task after installation was creating a secure Pi-hole admin password.

Ran the password command:
````
sudo pihole setpassword
````
Entered and confirmed the new password.
This password is required to log into the Pi-hole web interface.

⸻

2. Verifying Pi-hole Services

After installation and password setup, Pi-hole services were checked:
````
pihole status
````
A healthy system showed:
	•	DNS service: active
	•	FTL engine: running
	•	Web interface: available

If services were inactive, they could be restarted with:
````
sudo systemctl restart pihole-FTL
````
⸻

3. Accessing the Web Dashboard

The Pi-hole dashboard was accessed from a browser on the same network:
````
http://<pi-ip-address>/admin
````
Example (used during setup):
````
http://10.0.0.39/admin
````
Successful login confirmed that:
	•	The web server was running
	•	The password was applied correctly
	•	DNS statistics and query logs were visible

⸻

4. Confirming DNS Queries

To verify that Pi-hole was receiving traffic, the dashboard’s query log was inspected.

Key observations:
	•	Queries appeared from test Mac clients
	•	Local devices were listed under “Clients”
	•	Blocked domains were counted under “Queries Blocked”

These tests confirmed that Pi-hole was working as the upstream DNS resolver.

⸻

5. Troubleshooting Login Issues

During setup, several login issues were encountered and resolved.

Issue: Wrong Password Error

Occurred when Pi-hole cached an old password after resets.

Fix:
````
sudo pihole setpassword
````
This reset the password and restored access.

Issue: Blank Login Not Working

Earlier in the build, Pi-hole accepted a blank password.
After configuration changes, this behavior stopped.

Resolution involved resetting the credential file and setting a proper password.

⸻

Summary

At the end of this stage, the system was:
	•	Fully accessible through the web interface
	•	Configured with a secure admin password
	•	Running active DNS and FTL services
	•	Showing live queries from client devices
	•	Ready for DNS testing and network-wide deployment
