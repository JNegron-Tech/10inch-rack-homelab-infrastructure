# 10-Inch Rack Homelab Infrastructure

This repository documents a home lab designed to simulate real-world IT infrastructure and operational scenarios.

The lab is built in a physical **10-inch rack environment** and uses virtualization, segmented networking, and multiple operating systems to replicate enterprise infrastructure.

### Overall Lab Completion

Progress: **2 / 20 Projects Completed**

████░░░░░░░░░░░░░░░░░░ 10%


## 📈 Lab Progress Tracker

This homelab is an ongoing infrastructure project designed to simulate real-world IT environments.
The tracker below highlights the current progress of implemented systems and planned expansions.

| Category               | Project                                  | Status    |
| ---------------------- | ---------------------------------------- | --------- |
| Infrastructure         | Proxmox Infrastructure Host Deployment   | ✅ Completed |
| Infrastructure         | VLAN Network Segmentation                | ✅ Completed |
| Infrastructure         | Linux Server Deployment                  | 🟨 In Progress |
| Infrastructure         | Infrastructure Documentation             | 🟨 In Progress |
| Windows Infrastructure | Active Directory Domain Lab              | ⬜ Planned |
| Linux Administration   | Secure Access Management (SSH Hardening) | ⬜ Planned |
| Linux Administration   | Host-Based Firewall Implementation       | ⬜ Planned |
| Linux Administration   | Internal DNS & DHCP Services             | ⬜ Planned |
| Linux Administration   | Centralized File Server                  | ⬜ Planned |
| Security               | SSH Brute-Force Mitigation (Fail2ban)    | ⬜ Planned |
| Security               | SELinux Policy Management                | ⬜ Planned |
| Security               | Network Traffic Analysis                 | ⬜ Planned |
| Monitoring             | Infrastructure Monitoring Stack          | ⬜ Planned |
| Automation             | Backup Automation Scripts                | ⬜ Planned |
| Automation             | System Health Check Automation           | ⬜ Planned |
| Automation             | Configuration Management with Ansible    | ⬜ Planned |
| Automation             | Service Lifecycle Automation             | ⬜ Planned |
| Incident Response      | Disk Exhaustion Incident Simulation      | ⬜ Planned |
| Incident Response      | Critical Service Outage Recovery         | ⬜ Planned |
| Incident Response      | Security Incident Investigation          | ⬜ Planned |

### Status Legend

| Symbol         | Meaning                          |
| -------------- | -------------------------------- |
| ⬜ Planned      | Project has not started          |
| 🟨 In Progress | Currently being implemented      |
| ✅ Completed    | Fully implemented and documented |



---

# Lab Architecture

![Network](https://github.com/JNegron-Tech/10inch-rack-homelab-infrastructure/blob/3a066b0d4660fd9fe4388e82e6822e4d0977ea9b/images/Rack_Layout)


![10in Rack](https://github.com/JNegron-Tech/10inch-rack-homelab-infrastructure/blob/0be826285660b6cf773dbf00b5930c92a877f707/images/10in_Rack_Actual.jpg)

---

# Infrastructure Projects

| Project | Description |
|------|------|
| [Proxmox Infrastructure Host](infrastructure/proxmox-host-build.md) | Deploying and configuring the virtualization host |
| [VLAN Segmented Network](infrastructure/vlan-network-segmentation.md) | Implementing network segmentation |
| [Linux Server Deployment](infrastructure/linux-server-deployment.md) | Multi-distribution Linux infrastructure |

---

# Linux Administration

| Project | Description |
|------|------|
| [Secure Access Management](linux-admin/ssh-hardening.md) | SSH hardening and access control |
| [Host Firewalls](linux-admin/host-firewalls.md) | Implementing UFW and Firewalld |
| [DNS & DHCP Services](linux-admin/dns-dhcp-services.md) | Internal network services |

---

# Security Projects

| Project | Description |
|------|------|
| [Fail2ban Intrusion Prevention](security/fail2ban-intrusion-prevention.md) | Protecting SSH from brute-force attacks |
| [SELinux Policy Management](security/selinux-policy-management.md) | Enforcing mandatory access controls |
| [Network Traffic Analysis](security/network-traffic-analysis.md) | Packet inspection and troubleshooting |

---

# Automation

| Project | Description |
|------|------|
| [Backup Automation](automation/backup-automation.md) | Automated backup scripts |
| [System Health Checks](automation/system-health-checks.md) | Monitoring via scripts |
| [Ansible Automation](automation/ansible-automation.md) | Infrastructure configuration management |

---

# Windows Infrastructure

| Project | Description |
|------|------|
| [Active Directory Lab](windows-ad/active-directory-lab.md) | Windows domain services and group policy |

---

# Incident Response Scenarios

| Scenario | Description |
|------|------|
| [Disk Exhaustion Incident](incidents/disk-exhaustion-incident.md) | Responding to storage failures |
| [Service Outage Recovery](incidents/service-outage-recovery.md) | Recovering critical services |
| [Security Incident Simulation](incidents/security-incident-response.md) | Investigating unauthorized access |
