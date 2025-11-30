01 – Pi-hole Installation

This document covers how Pi-hole was installed on the Raspberry Pi 5, from package preparation to initial service startup.

⸻

1. Preparing the System

Before installing Pi-hole, the system was updated to ensure all packages were current.
````
sudo apt update
````
````
sudo apt update -y
````
The Raspberry Pi was confirmed to have a working internet connection and stable SSH access.

⸻

2. Downloading and Running the Pi-hole Installer

Pi-hole provides an official installation script that automates setup.

The installer was launched with:
````
curl -sSL https://install.pi-hole.net | bash
````
The script guided the installation and prompted for several configuration choices.

⸻

3. Key Installation Options Selected

During installation, the following options were chosen:

• Upstream DNS provider

Cloudflare (1.1.1.1 and 1.0.0.1) was selected for speed and privacy.

• Block lists

Pi-hole’s default blocklist was enabled.

• Admin Web Interface

The web dashboard was installed for monitoring and management.

• Web Server

Lighttpd was installed automatically to support the admin interface.

• Logging

Query logging was enabled.

These defaults provided a solid configuration for a first-time deployment.

⸻

4. Installation Completion

After installation, Pi-hole displayed the admin interface address and a temporary password.

Example output:
````
http://<pi-ip-address>/admin
````
The system reported a successful installation, and Pi-hole services were verified with:
````
pihole status
````

⸻

Summary

At the end of installation:

• Pi-hole packages were installed
• The dashboard and web server were active
• DNS blocking lists were loaded
• A default admin password was generated
• The Raspberry Pi was ready for configuration and DNS testing
