# Mini SOC lab: SSH-Brute-Force-Attack-Detection-and-Mitigation
I built a mini SOC lab to simulate a real-world attack. 
I used to laptops on the same network, 
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

*Wazuh logging:*
I started wazuh-agent for alerts to be sent to Wazuh dashboard 

*Attack:*
Ran Hydra SSH brute-force and it found the password. 

*Detection:*
Checked the auth.logs to see failed ssh login attempts from the attacker IP in real-time
wazuh dashboard visualized the failed attempts. 

*Mitigation:* Blocked attacker IP with iptables
