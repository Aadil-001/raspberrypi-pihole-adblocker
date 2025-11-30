04 – Disable or Uninstall Pi-hole

This document explains the steps taken to disable Pi-hole, stop its services, and prepare the Raspberry Pi for shutdown after testing.

1. Disabling Pi-hole from the CLI

Pi-hole includes a built-in disable command.
This was used to stop DNS blocking:
````
pihole disable
````
This disabled Pi-hole immediately and confirmed the action in the terminal.

2. Stopping the FTL Service

To fully shut down Pi-hole’s DNS resolver, the FTL engine was stopped:
````
sudo systemctl stop pihole-FTL
````
This ensured Pi-hole was no longer handling DNS queries or responding to clients.

3. Verifying Deactivation

To confirm Pi-hole was no longer active:
````
pihole status
````
Expected output showed:
	•	DNS service: inactive
	•	FTL engine: not running
	•	Web interface: still installed, but backend inactive

These checks verified Pi-hole had been safely disabled.

4. Network Behavior After Disabling

After disabling Pi-hole, DNS traffic returned to using the router’s upstream resolver.

Observed during tests:
	•	Client devices immediately fell back to default DNS
	•	Web browsing returned to normal without filtering
	•	No DNS resolution errors were seen

5. Preparing the Raspberry Pi for Shutdown

Once testing was complete, the Raspberry Pi was prepared for safe shutdown.

Checked active processes:
````
ps aux | grep pihole
````
If any Pi-hole processes were still present, they were stopped before powering off.

Shutdown procedure:
````
sudo shutdown now
````
This ensured the system powered down safely before unplugging.

⸻

Summary

At the end of this stage:
	•	Pi-hole was fully disabled
	•	DNS traffic returned to normal routing
	•	FTL service was stopped cleanly
	•	System was shut down safely
	•	The Raspberry Pi was ready for storage or future use
