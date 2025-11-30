03 – DNS Testing and Verification

This document explains how DNS behavior was tested after Pi-hole installation to confirm that the device was resolving domains correctly and blocking unwanted traffic.

1. Verifying Pi-hole as the DNS Resolver

To confirm Pi-hole was handling DNS requests, several tests were run from the Raspberry Pi.

Checked DNS resolution for a known domain:

nslookup google.com

Typical expected output:
- Server: <pi-hole-ip>
- Address: <pi-hole-ip>#53
- Non-authoritative answer returned by upstream resolver

This confirmed that Pi-hole was processing DNS queries.

2. Testing Blocked Domains

To verify ad blocking worked, a known ad-serving domain was queried:

nslookup doubleclick.net

Expected behavior:
- Pi-hole returned ````0.0.0.0```` or ````0.0.0.1````
- Domain appeared under the Pi-hole dashboard's “Queries Blocked” list

This confirmed blocklists were functioning correctly.

3. Testing DNS from Client Devices

The next step was verifying DNS from other devices on the network.

From a Mac:

````nslookup google.com <pi-hole-ip>````

From iPhone (using Pi-hole as DNS):
- Browsed to several sites
- Confirmed ads were reduced
- Confirmed blocked queries increased on the Pi-hole dashboard

These tests verified that client devices were successfully using Pi-hole as their DNS resolver.

4. Latency and Reliability Checks

Ensured DNS response times were stable:

````ping <pi-hole-ip>````

Confirmed consistent millisecond-level response times.

If latency increased, logs were checked in:

````/var/log/pihole-FTL.log````

5. Dashboard Inspection

Monitored Pi-hole’s live query logs:
- Verified continuous queries from multiple clients
- Checked upstream resolver performance
- Ensured no errors or rate limiting messages appeared

Summary

At the end of this stage, DNS was:
- Successfully routed through Pi-hole
- Blocking known ad and tracker domains
- Serving valid upstream DNS responses
- Confirmed from both the Raspberry Pi and client devices
- Stable and ready for network-wide deployment
