# Mini SOC lab: SSH-Brute-Force-Attack-Detection-and-Mitigation
I built a mini SOC lab to simulate a real-world attack. 
I used two laptops on the same network, 
one as attacker machine running Hydra for SSH brute-force
and the other as the victim(Ubuntu VM). The attack was detected in real-time
using Wazuh SIEM via auth.log monitoring, 
and successfully mitigated using iptables to block the attacker IP. 

##Lab Setup
1. Attacker: Kali Linux
2. Victim: Ubuntu VM
3. same Lan network

##Steps 

*Ping Test and Nmap:*
I ran a Ping test to see if the host is up and ran nmap port scan on the host IP to see open ports. 
![Ping test and nmap scan](./ping_test_nmap.JPG)

*Wazuh logging:*
I started Wazuh-agent to send alerts to SIEM dashboard.

*Attack:* Ran Hydra SSH brute-force against the Victim IP address and found the correct password. I used the correct password found by Hydra to gain access to the victim machine via SSH

*Detection:*
Checked the auth.logs to see failed ssh login attempts from the attacker IP in real-time and also a successful login from the Attacker IP after the numerous failed ones 

wazuh dashboard visualized the failed attempts. and the successful login 

*Mitigation:* Blocked attacker IP with iptables
