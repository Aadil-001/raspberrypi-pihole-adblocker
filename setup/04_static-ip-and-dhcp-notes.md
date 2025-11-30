04 – Static IP and DHCP Notes

This document explains how the Raspberry Pi’s IP behavior was observed during setup, why static IP planning became necessary, and how DHCP leases behaved on the home network.

⸻

1. DHCP Behavior Observed During Setup

When the Raspberry Pi 5 first connected to Wi-Fi, the router assigned it an address in the 10.0.0.x range.

Key behavior during testing:

• The Pi initially received 10.0.0.39
• After some reboots, it reassigned to 10.0.0.40
• At other times, the entry appeared as (incomplete) in ARP scans
• The Orbi mesh system and AT&T router both influenced DHCP assignments
• Device visibility fluctuated between Orbi nodes during reconnects

This inconsistent assignment motivated the move toward a static IP.

⸻

2. Tracking the Pi’s IP Address

To track the current DHCP-assigned address, the following commands were used:

Check the Pi’s hostname:
````
hostname -I
````
Scan local devices from a Mac:
````
arp -a
````
When the Pi’s IP changed after reboot, the ARP scan was the fastest way to rediscover it.

⸻

3. Router and Mesh Network Notes

During setup, both an AT&T gateway and Orbi mesh system were active on the network.

Observed behavior:

• Devices appeared under different DHCP pools depending on which device responded
• Orbi sometimes masked devices behind its own MAC until refreshed
• The Pi occasionally failed to rejoin Wi-Fi until physically power-cycled
• ARP entries for the Pi timed out faster than expected

These behaviors suggested the network would benefit from a dedicated static reservation for the Pi.

⸻

4. Why Use a Static IP for Pi-hole

Pi-hole must run at a consistent IP address so clients can reach it reliably.

Without a static IP:

• DNS requests can be sent to the wrong address
• Clients experience lost connectivity
• SSH access becomes inconsistent
• Troubleshooting becomes harder

By planning a static IP (for example, 10.0.0.50), future Pi-hole sessions become stable.

A static IP can be assigned later using either the Pi’s dhcpcd.conf or the router’s DHCP reservation page.

⸻

5. Reliability Tests Before Finalizing Static IP

Before setting the permanent address, several tests confirmed the network was stable enough for Pi-hole:

Ping to the router:
````
ping 10.0.0.1
````
DNS lookup through the router:
````
nslookup google.com
````
Wi-Fi interface check:
````
ip a
````
Once these were consistently stable, Pi-hole installation proceeded.

⸻

Summary

At the end of this stage:

• DHCP behavior was understood
• The Pi’s changing IP addresses were documented
• Network topology between AT&T and Orbi equipment was observed
• A static IP plan was selected for a reliable Pi-hole service
• The system was ready for Pi-hole installation and DNS configuration
