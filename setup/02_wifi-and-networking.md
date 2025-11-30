1. Verifying Wi-Fi Connectivity
   After SSH access was established, the first task was confirming that the Pi had a stable Wi-Fi connection.

Checked interface status:
````
ip a
````
Confirmed the Pi received an IP address in the expected range.

Tested connectivity to the router:
````
ping 10.0.0.1
````
Tested outbound internet connectivity: 
````
ping google.com
````
All responses confirmed that Wi-Fi was working correctly.

---

2. Checking the Pi’s Current IP Address

Identified the current DHCP-assigned address:
````
hostname -I
````
This helped track how the IP was appearing on the network and verify stability across reboots. 

3. Router and Network Observations

---

During setup, FIOS/AT&T equipment and Orbi mesh nodes were in use.
Key observations:

• Devices appeared under 10.0.0.x
• The Pi initially used 10.0.0.39
• After reboot, the Pi sometimes reassigned to another address
• ARP scans were used to find the Pi again when needed:
````
arp -a
````
This motivated the later move toward static IP planning. 

---

4. DNS Behavior Before Pi-hole

Before installing Pi-hole, testing showed that all devices used the router as their DNS resolver:
````
nslookup google.com
````
Typical output displayed: 
````
Server: 10.0.0.1
Address: 10.0.0.1#53
````
Confirming the router was handling DNS upstream. 

---

Summary

At the end of this stage:

• Wi-Fi was stable
• The Pi’s IP address was identified
• Router and mesh network behavior were understood
• DNS traffic flow was confirmed
• The system was ready for SSH hardening, static IP decisions, and Pi-hole installation
