DeauthKismet

DeauthKismet is a minimal, research-focused project that demonstrates how to detect Wi-Fi Deauthentication (Deauth) Denial-of-Service (DoS) attacks using Kismet in a controlled lab environment.

> This project is intended strictly for ethical use, academic research, and educational purposes only.




---

Objective

To monitor and identify Deauthentication (Deauth) attack patterns on wireless networks using passive detection techniques, specifically with Kismet, combined with standard Wi-Fi auditing tools for setup and simulation.


---

Prerequisites
- Kali Linux, Parrot OS, or any Linux distro with:

• aircrack-ng suite (airmon-ng, airodump-ng, aireplay-ng)

• iwconfig

• kismet


- A wireless adapter that supports monitor mode and packet injection

- Lab Wi-Fi environment (Do not perform on unauthorized networks)



---

Step-by-Step Instructions

Step 1: Kill Conflicting Services and Enable Monitor Mode

Purpose: Prepare your wireless adapter for monitoring.

**sudo airmon-ng check kill**
**sudo airmon-ng start wlan0**

This will create a monitor mode interface like wlan0mon.


---

Step 2: Scan for Available Wi-Fi Networks

Purpose: Identify your target access point’s BSSID and channel.

**sudo airodump-ng wlan0mon**


---

Step 3: Set Wireless Interface to Fixed Channel

Purpose: Ensure accurate monitoring on a single channel.

**sudo iwconfig wlan0mon channel <channel_number>**

Replace <channel_number> with the correct channel.


---

Step 4: Simulate a Deauthentication Attack (Lab Only)

Purpose: Generate deauth packets to test detection setup.

**sudo aireplay-ng --deauth 0 -a <BSSID> wlan0mon**

Replace <BSSID> with the target access point MAC address.
Only perform this in a lab environment.


---

Step 5: Launch Kismet for Detection

Purpose: Use Kismet to passively monitor deauth attacks.

**sudo kismet**

Then in the Kismet UI:

• Select Add Source

• Choose your monitor interface (e.g., wlan0mon)

• Begin monitoring



---

Step 6: Analyze Results

Purpose: Detect and confirm deauth attacks.

• Kismet will show alerts for deauth traffic.

• Review logs and timestamps for verification.



---

Video Demonstration

Watch the full lab demonstration on the TurbineShield YouTube channel:
https://youtube.com/@TurbineShieldSec


---

Disclaimer

This project is for educational and ethical use only. Performing attacks on unauthorized networks is illegal and unethical. Always test in a controlled, permissioned environment.


---

License

This project is licensed under the MIT License.
