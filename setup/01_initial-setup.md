# 01 – Initial Raspberry Pi Setup

This document covers the very first steps taken before installing Pi-hole or configuring networking.  
These actions prepared the Raspberry Pi 5 for all later work.

---

## 1. Flashing Raspberry Pi OS

• Used the Raspberry Pi Imager  
• Selected **Raspberry Pi OS (64-bit)**  
• Enabled:  
  – Set username and password  
  – Enable SSH  
  – Configure Wi-Fi  
  – Set locale and timezone  

The Pi booted headless with no monitor or keyboard needed.

---

## 2. First Boot

After powering on the Pi:

• Waited for it to appear on the network  
• Connected through SSH using the hostname created in Imager:
````
ssh black_pearl_captain@
````
• Verified the Pi was reachable with:  
````
ping 
````
---

## 3. System Updates

Before installing anything:
````
sudo apt update
````
````
sudo apt update -y
````

This ensured the Pi had the latest security patches and package versions.

---

## 4. Basic System Checks

Verified the hardware was healthy by running:

````
uname -a
````
````
uptime
````
````
df -h
````

Also confirmed that SSH login was stable and network latency was normal.

---

## Summary

At the end of this stage, the Raspberry Pi was:

• Flashed  
• Configured for headless operation  
• Updated  
• Reachable over SSH  
• Ready for networking and Pi-hole installation
