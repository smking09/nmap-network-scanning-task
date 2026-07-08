# nmap-network-scanning-task
Task 1: Basic Network Scanning with Nmap

Objective

Perform a network scan to identify open ports and running services on a local machine using Nmap, and document the findings with a security analysis of each discovered service.

What is Nmap?

Nmap ("Network Mapper") is a free, open-source tool used to discover devices on a network and gather information about them — such as which ports are open, what services/software are running behind those ports, and what operating system a device is likely running. It's one of the most widely used tools in cybersecurity for network reconnaissance, vulnerability assessment, and penetration testing.

Why Network Scanning Matters

Before a system or network can be secured, defenders need to know what is actually exposed to the network. Every open port is a potential entry point. Network scanning allows security professionals and administrators to:


Discover unexpected or forgotten services running on a machine
Identify outdated software versions that may carry known vulnerabilities
Verify that firewall rules are working as intended
Build an accurate picture of a system's "attack surface" before attackers do


Attackers use the exact same technique as a first step before attempting an intrusion, which is why scanning your own systems proactively is a core defensive practice.

Environment / Setup


Host tool used: VirtualBox
Target/Scanner OS: Kali Linux (VM)
Nmap Installation: Kali Linux ships with Nmap pre-installed. No manual installation was required. Verified with:


bashnmap --version
# Output: Nmap version 7.99 ( https://nmap.org )


Target scanned: The Kali VM itself (10.0.2.15). A second machine was not available for this exercise, so the VM was scanned against its own IP address as a safe, fully authorized alternative (see Ethics Note below).
Service enabled for testing purposes:


bashsudo systemctl start ssh
sudo systemctl enable ssh

This turned on the SSH service (off by default on Kali) so that the scan would have a real, open port and running service to analyze.

Scans Performed


Basic scan — nmap 10.0.2.15 — identifies open ports
Service version scan — sudo nmap -sV 10.0.2.15 — identifies the software and version running on each open port
OS detection scan — sudo nmap -O 10.0.2.15 — attempts to fingerprint the target's operating system


Full output of all three scans, the list of open ports, and a port-by-port security analysis are documented in nmap_scan_results.txt.

Terminal screenshots of each scan are included in the screenshots/ folder.

Summary of Findings

PortServiceVersionRisk Level22/tcpSSHOpenSSH 8.9p1 (Debian 4)Low-Medium

Only one port was open (SSH, manually enabled for this exercise). All other commonly-checked ports were filtered, indicating a restrictive default firewall posture. Full risk analysis is in nmap_scan_results.txt.

⚠️ Ethics Note

Network scanning should only ever be performed on systems you own or have explicit, documented permission to test. Scanning devices, networks, or servers that you do not own or have not been authorized to test — even "just to see what happens" — can be illegal in most jurisdictions (e.g., under laws such as the U.S. Computer Fraud and Abuse Act) and can be treated the same as a real attack, regardless of intent.

For this reason:


All scans in this task were performed exclusively against a personal Kali Linux VM, which is fully owned and controlled by the person completing this exercise.
No external, third-party, or production systems were scanned at any point.
This project is for educational purposes only, intended to build foundational understanding of how network reconnaissance tools work.


Tools Used


Nmap 7.99
Kali Linux (VirtualBox VM)



Task completed by Smarak Bhandari — Oasis Infobyte Security Analyst Internship, July 2026.
