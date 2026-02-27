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

  Here Is a Simple diagram outlining the basic network layout.
![Network Diagram](https://github.com/user-attachments/assets/72a44d31-c1ff-4b48-9acd-55a32852b0ec)


  I will quickly go through all of the machines that I created for this lab, they were all created using Oracle Virtualbox.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 144356" src="https://github.com/user-attachments/assets/ed06adf8-4b95-426f-b7d4-7873edb2389b" />
I first set up an OPNsense machine. This machine is my firewall/gateway, it allows me to control access to the internet when needed, and keep the the network closed off from the outside world otherwise. It also has Suricata installed, which will be included in greater detail in a project focused specifically on IDS/IPS.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 145005" src="https://github.com/user-attachments/assets/755950f3-6424-45ab-9095-78d41a8561bb" />
The next machine is an Ubuntu 22.04 desktop machine, which is where I installed the Wazuh manager, as well as OpenVAS, and was primarily the workhorse machine I used to configure all the systems.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 144816" src="https://github.com/user-attachments/assets/da4baff2-5087-4c1f-9203-8e37d72be297" />
This next machine is a Ubuntu 22.04 server VM which is very barebones, I used it solely to host OsTicket, that way I could emulate a ticketing system workflow.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 145155" src="https://github.com/user-attachments/assets/76718ee9-1214-4cf2-a9c8-c16815341302" />
Now for the two machines which will be emulation real world scenerios. First is this Kali Linux VM which is places on its own seperate LAN in order to emulate an outside attack. This machine is the primary one I will use to carry out attacks in my other projects that will be using this lab.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 144519" src="https://github.com/user-attachments/assets/64087fc1-4f97-4e36-b55d-f2a3455b7682" />
The last machine is this Windows 11 VM, and its primary goal is to be the target. It is a Wazuh agent, and it is also a target for OpenVAS scans.
<img width="1920" height="1032" alt="Screenshot 2026-02-24 144643" src="https://github.com/user-attachments/assets/7ecdbc3a-ccd4-4771-92cf-729e76a96764" />

