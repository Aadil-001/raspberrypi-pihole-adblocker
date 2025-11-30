# Raspberry Pi 5 Pi-hole Ad-Blocking System

This project documents how I built, configured, tested, and managed a complete DNS-based ad-blocking solution on a Raspberry Pi 5 using Pi-hole.  
It includes setup notes, configuration steps, network testing, troubleshooting logs, and lessons learned.

---

## Project Goal
Create a reliable network-wide ad blocker using Pi-hole on a Raspberry Pi 5 to better understand DNS, DHCP, Linux networking, SSH, and home-lab system management.

---

## Repository Structure

```
raspberrypi-pihole-adblocker/
├── README.md
├── images/
│   └── screenshots and reference images
├── setup/
│   ├── 01_initial-setup.md
│   ├── 02_wifi-and-networking.md
│   ├── 03_ssh-setup.md
│   └── 04_static-ip-and-dhcp-notes.md
├── pihole/
│   ├── 01_installation.md
│   ├── 02_configuration.md
│   ├── 03_dns-testing.md
│   ├── 04_disable-or-uninstall.md
│   └── 05_troubleshooting-log.md
└── logs/
    ├── day1-terminal-log.md
    ├── network-events.md
    └── lessons-learned.md
```eoD
---

## Skills Demonstrated

### Linux Fundamentals
- Command-line navigation
- Service management with `systemctl`
- Editing system files with nano
- Managing logs and debugging errors

### Networking Concepts
- DNS resolution flow  
- DHCP vs. static IP planning  
- Local network device discovery and ARP table analysis  
- Using tools like `ping`, `nslookup`, `arp`, and Pi-hole logs

### Raspberry Pi System Management
- Headless setup  
- SSH access  
- Package management  
- Service installation and cleanup  

### GitHub Project Organization
- Clean folder-based documentation  
- Log archiving  
- Multi-file Markdown documentation  

---

## Why this project matters

This project provided hands-on experience with:
- DNS-level ad blocking  
- Real-world troubleshooting of Linux services  
- Network analysis  
- Managing a Raspberry Pi as a real service device  
- Documenting technical work clearly for resume and personal development  

---

## Screenshots
All screenshots are stored in the `images/` folder for reference.

---

## Future Improvements
- Add automated backup scripts  
- Configure Grafana dashboards for DNS analytics  
- Explore additional Raspberry Pi projects using the same hardware  

---

## License
This project is documented for educational and portfolio purposes.
