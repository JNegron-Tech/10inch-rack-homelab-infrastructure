# 🖥️ Proxmox VE Deployment & OPNsense VM Setup

## 📌 Project Overview

This repository documents the deployment of **Proxmox VE** as a virtualization host and the installation of **OPNsense** as a virtualized firewall for VLAN-segmented lab networks. The goal was to create a **scalable, enterprise-style lab environment** with isolated VLANs routed through a secure firewall.

This write-up includes:

- Proxmox installation and initial configuration  
- Network bridge setup for VLANs  
- OPNsense VM creation and network attachment  
- Troubleshooting notes and lessons learned  

---

## 🧰 Hardware & Tools

- **Hypervisor:** Proxmox VE 7.x  
- **Physical Host NICs:** enp3s0 (management), enp1s0f0 (LAN / lab VLAN), enp1s0f1 (WAN)  
- **Firewall:** OPNsense VM  
- **Managed Switch:** TP-Link SG105E  
- **Client Machine:** Parrot OS (for VLAN 10 testing)  

---

## ⚙️ Proxmox Host Deployment

### 1. Installation

- Installed Proxmox VE from ISO on the host machine.  
- Configured hostname, root password, storage, and basic network during installation.  
- Verified network connectivity on the management interface (`enp3s0`) using IP `192.168.8.10`.  

---

### 2. Network Configuration

- Created **vmbr0**:  
  - Bridged to `enp3s0`  
  - Not VLAN-aware  
  - Auto-start enabled  
  - Gateway: `192.168.8.1`  

- Created **vmbrLAN** (for OPNsense LAN / VLAN 10):  
  - Bridged to `enp1s0f0`  
  - Not VLAN-aware (untagged VLAN 10)  
  - Auto-start enabled  

- Ensured `enp1s0f1` remained as a separate NIC for OPNsense WAN connection.  

---

### 3. OPNsense VM Creation

- Created a new VM in Proxmox VE.  
- Allocated resources:  
  - CPU: 2 cores  
  - Memory: 2 GB  
  - Disk: 16 GB  
- Added network interfaces:  
  - LAN NIC → `vmbrLAN`, firewall enabled  
  - WAN NIC → `enp1s0f1` directly (no bridge)  
- Mounted OPNsense ISO and booted the VM for installation.  

---

### 4. Initial OPNsense Configuration

- Completed the setup wizard:  
  - WAN: DHCP from GL.iNet router  
  - LAN: Static IP `192.168.10.1`, DHCP enabled for lab clients  

- Verified network connectivity:  
  - OPNsense WAN IP: `192.168.8.156`  
  - LAN IP accessible from VLAN 10 client (`192.168.10.10`)  

---

## 🧪 Troubleshooting Notes

- **NIC conflicts:** Initial attempts to attach VLAN 10 to `vmbr0` failed. Resolved by creating `vmbrLAN` on a dedicated NIC (`enp1s0f0`).  
- **Link down issues:** Switch port 4 had no activity; resolved by bringing the NIC up with `ip link set enp1s0f0 up`.  
- **VLAN tagging:** OPNsense LAN NIC configured untagged to match switch port VLAN 10.  
- **Connectivity validation:** Stepwise testing from host → VM → client → WAN to ensure proper routing and isolation.  

---

## 💡 Lessons Learned

1. Always verify the **physical layer** before debugging VLANs or bridges.  
2. Use **dedicated NICs per VLAN** to simplify configuration and avoid conflicts.  
3. Test connectivity incrementally: Proxmox host → VM → client → firewall → internet.  
4. Document every bridge, VLAN, and IP assignment to avoid confusion later.  

---

## 🚀 Next Steps

- Implement firewall rules to secure VLAN 10 and protect the management network.  
- Expand lab with additional VLANs for servers, DMZ, or lab experiments.  
- Take screenshots at key steps for future portfolio updates.  
- Consider automating deployments with Ansible or cloud-init for reproducibility.
