# Cybersecurity Home Lab

## Objective
This Cybersecurity home lab configuration project focuses on designing and constructing the systems that make up a fundamental SOC. The goal is was to create virtual environment where I could test out multiple different security systems. In this project I deploy virtual machines and configure multiple networks in order to create an invironment where I can simulate external threats. In this environment, I also configured some important security tools, such as Wazuh, Suricata, OpenVAS and OsTicket, and created workflows from these systems to automatically create tickets in OsTicket.

### Skills Learned

- Network Engineering: Implementation of multi-interface firewalls and virtual network adapters to create isolated broadcast domains.
- System Integration: Establishing cross-platform telemetry paths between OPNsense, Wazuh, and osTicket via Syslog and Webhooks.
- Hardened Infrastructure: Deploying and managing security tools within Docker containers and Linux server environments.
- SOC Orchestration: Designing an automated alerting pipeline where network (Suricata), endpoint (Wazuh), and vulnerability (OpenVAS) data converge into a single ticketing system.

### Tools Used

- OPNsense: An open-source firewall and routing platform configured as the network gateway to manage inter-VLAN routing and perimeter security.
- Suricata: A network threat detection engine integrated into the gateway to provide signature-based Intrusion Detection (IDS).
- Wazuh: A centralized SIEM/XDR manager used for cross-platform log aggregation, file integrity monitoring, and security orchestration.
- Greenbone (OpenVAS): A comprehensive vulnerability management suite used for infrastructure-wide security assessments.
- osTicket: An open-source ITSM platform used for centralizing and managing the lifecycle of security incidents.
- Kali Linux: A specialized penetration testing distribution used to generate controlled attack traffic from a segregated network segment.
- Ubuntu Server: The core Linux backbone used to host the osTicket server, manage containerized services, and provide a stable environment for centralized log storage.
- Oracle VirtualBox: The Type-2 hypervisor used to manage the virtual hardware and internal networking for all lab segments.
- Python 3: Used for developing custom integration scripts to facilitate communication between isolated security tools.

## Steps
This section will be more of a description of the home lab that I built, which allows me to to experiment with different cybersecurity tools and systems. I will go through all of the virtual machines and systems involved in this home lab, as well as the workflows used to direct alerts to Wazuh and OsTicket. I do want to note that if resources were unlimited, I would have gone more in depth with the network construction (ie. assigning an individual firewall to each network, and having the Wazuh manager on a seperate network, where the firewall allows access only from machines that need to interact.) but I am running all of these VMs on my personal computer, so resources are limited.

<img width="759" height="361" alt="Screenshot 2025-07-28 212829" src="https://github.com/user-attachments/assets/b4f897e2-025f-4be3-84c0-1f81e5cc2172" />
