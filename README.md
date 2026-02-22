# Cybersecurity Home Lab

## Objective
This Cybersecurity home lab configuration project focuses on designing and constructing the systems that make up a fundamental SOC. the goal is was to create virtual environment where I could test out multiple different security systems. In this project I deploy virtual machines and configure multiple networks in order to create an invironment where I can simulate external threats.

### Skills Learned

- Fundamantal understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
I started by installing Sysmon on my windows 11 VM. Sysmon is a Windows tool that generates telemetry on system activity to help with threat detection and monitoring.

My next step was to create a cloud based VM with Ubuntu 22.04 installed, I would use this machine as my Wazuh manager. (I used DigitalOcean for my VM's, please excuse the other two, they will come up in my Automation Project.)

<img width="759" height="361" alt="Screenshot 2025-07-28 212829" src="https://github.com/user-attachments/assets/b4f897e2-025f-4be3-84c0-1f81e5cc2172" />
