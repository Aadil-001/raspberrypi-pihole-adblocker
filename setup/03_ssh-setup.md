03 – SSH Setup and Secure Access

This document describes how SSH access was configured, tested, and secured on the Raspberry Pi 5.

⸻

1. Enabling SSH

SSH was enabled in the Raspberry Pi Imager before flashing the SD card.

Configured options included:

• Enable SSH
• Set username
• Set password

This allowed headless access immediately after first boot.

⸻

2. Finding the Raspberry Pi on the Network

Once the Pi powered on, the next task was locating it on Wi-Fi.

Checked local devices with:
````
arp -a
````
The Pi appeared under addresses in the 10.0.0.x range.

If it was not visible, a reboot and another ARP scan helped rediscover the device.

⸻

3. Connecting with SSH

Used SSH from a Mac terminal to log into the Pi:
````
ssh black_pearl_captain@10.0.0.39
````
If the IP changed after reboot:

• Tried previous known addresses
• Used arp -a to look for the Pi’s MAC address
• Used the new IP with SSH

SSH login was successful when the Pi responded to ping:
````
ping 10.0.0.x
````

⸻

4. Troubleshooting SSH Connection Issues

During setup, several connection problems were observed:

Issue: “Operation timed out”

Occurred when the Pi changed its IP after reboot.

Solution:
Find the new address using:
````
arp -a
````
Issue: “Host is down”

Happened when the Pi failed to reconnect to Wi-Fi.

Solution:
Unplug and replug the Pi, wait 30 seconds, then rescan the network.

Issue: Wrong username/password

Fixed by ensuring the correct credentials from the Imager setup were used.

⸻

5. Verifying SSH Stability

After successful login, confirmed the connection was stable by running:
````
uptime
````
````
````
````
hostname
````
SSH remained reliable once the network behavior was understood.

⸻

Summary

At the end of this stage:

• SSH was enabled and working
• The Pi’s IP address was successfully tracked
• Common network issues were diagnosed
• Reconnection steps were documented
• The system was ready for static IP configuration and Pi-hole installation
