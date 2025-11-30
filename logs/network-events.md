# Network Events and Observations Log

This log captures key networking events that occurred during the Raspberry Pi 5 Pi-hole build.  
It documents ARP behavior, DHCP changes, IP conflicts, and mesh network interactions across AT&T and Orbi systems.

---

## 1. DHCP Lease Changes

During setup, the Raspberry Pi frequently received different IP addresses from the router.

Observed patterns:

- Initial IP assignment was **10.0.0.39**
- After some reboots, the Pi moved to **10.0.0.40**
- At times, the Pi showed as “incomplete” in ARP tables
- The Orbi mesh and AT&T gateway both affected DHCP leases

These changes made SSH reconnects unreliable, which motivated the move toward a static IP plan.

---

## 2. ARP Scan Behavior

ARP scans were used often to rediscover the Pi when its IP changed.

Commands used:
````
arp -a
````
Key findings:

- Pi appeared under multiple MAC entries depending on mesh node  
- Orbi nodes sometimes responded instead of the Pi  
- When Wi-Fi rejoined after reboot, ARP entries updated slowly  
- Rediscovery required rescanning after 20–30 seconds

ARP behavior showed how mesh networks delay device discovery.

---

## 3. Mesh Network Effects (AT&T + Orbi)

Both the AT&T gateway and the Orbi mesh influenced connections.

Notable events:

- Devices appeared behind different Orbi nodes depending on location  
- Pi occasionally failed to reconnect to Wi-Fi until power-cycled  
- Some ARP entries timed out rapidly, then re-populated  
- DNS requests briefly failed during mesh handoffs

These patterns confirmed that Pi-hole would be more stable with a static IP reservation.

---

## 4. DNS Resolution Issues Before Static IP

Before assigning a static address, DNS queries sometimes routed to the wrong resolver.

Symptoms:

- nslookup results pointed to different gateway addresses  
- Queries occasionally bypassed Pi-hole  
- Dashboard showed inconsistent client sources  
- Some blocked domains briefly passed through

After setting the static IP plan, DNS routing stabilized.

---

## 5. Network Reliability Improvements Over Time

As configuration progressed, reliability increased:

- SSH reconnects became consistent  
- ARP discovery delays decreased  
- Pi-hole responded steadily on the static IP  
- Web dashboard access became predictable  
- DNS logs showed continuous traffic from all clients

The network stabilized once DHCP behavior was understood and addressed.

---

## Summary

At the end of testing, the network exhibited:

- Predictable DHCP behavior  
- Consistent ARP resolution  
- Stable DNS routing through Pi-hole  
- Reliable SSH and dashboard access  
- No further IP conflicts or mesh-related disruptions

The Raspberry Pi was fully ready for long-term Pi-hole operation.
