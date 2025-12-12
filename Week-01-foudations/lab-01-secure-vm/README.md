# Lab 01 — Secure Ubuntu VM Deployment (Azure)

## Overview
This lab demonstrates the deployment and security hardening of an Ubuntu virtual machine in Microsoft Azure. The goal is to practice resource provisioning, secure network configurations, SSH access, system updates, and cost-control settings that reflect real junior cloud engineering workflows.

## Architecture
- **1x Ubuntu VM** (Standard_D2s_v3 — 2 vCPUs, 8 GiB RAM)
- **Resource Group:** rg-week01-securevm
- **Region:** West US 2
- **Public IP:** Used for SSH access (restricted)
- **Network Security Group:** SSH allowed only from my IP
- **Auto-shutdown enabled:** Prevents unnecessary compute cost

---

## Deployment Steps

### 1. Resource Group Creation
Created the resource group:rg-week01-securevm


This isolates all resources related to Week 01 for easy management and cleanup.

---

### 2. Virtual Machine Deployment
- **Image:** Ubuntu Server 22.04 LTS  
- **Size:** Standard_D2s_v3  
- **Region:** West US 2  
- **Authentication:** Password  
- **Disk:** Standard HDD  
- **Public IP:** Enabled  
- **Auto-shutdown:** ON at 11 PM  

VM was deployed successfully using a D-series size due to B-series and A-series quota limitations.

---

### 3. Network Security Hardening (NSG)
Configured inbound network rules using Azure NSG:

- **Allow SSH (port 22)**  
  - Source: **My IP address only**  
  - Prevents all other internet traffic  
  - Reduces attack surface  
- All other unsolicited inbound traffic is blocked by default

This mirrors real-world least-privilege network security practices.

---

### 4. SSH Access & System Updates
Connected to the VM using:

ssh azureuser@<PUBLIC_IP_ADDRESS>


Once connected, performed system updates:

sudo apt update && sudo apt upgrade -y


This ensures the VM is fully patched and secure.

---

### 5. Screenshots
Screenshots are stored in the `screenshots/` folder:

- Resource Group creation  
- VM Review + Create page  
- Networking + NSG rule (My IP only)  
- Auto-shutdown settings  
- SSH terminal session  

These screenshots validate proper deployment and configuration.

---

## Key Concepts Demonstrated
- VM provisioning in Azure  
- Secure SSH access  
- Network Security Groups (NSGs)  
- Attack surface reduction  
- Cloud cost control  
- Resource organization (Resource Groups)  
- Basic Linux administration  

---

## Next Steps (Week 02)
- Build a virtual network (VNet)
- Create subnets
- Deploy multiple VMs into isolated networks
- Test internal-only communication with no public exposure
- Apply NSG rules at subnet level

These networking labs build directly on the foundation created in Lab 01.

---

