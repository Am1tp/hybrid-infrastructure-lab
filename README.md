# hybrid-infrastructure-lab

## Overview
A self-hosted enterprise-style hybrid infrastructure lab used to develop and demonstrate practical skills in networking, Linux administration, virtualisation, observability, automation and cloud-integrated operations.

The lab provides hands-on experience in:

- Network planning, implementation and management
- Routing, switching and VLAN segmentation
- Observability and monitoring
- Linux administration
- Virtualisation and self-hosted services
- Cloud-integrated and hybrid environments
- Troubleshooting and operational workflows
- Documentation and architecture design

---

## Current Infrastructure

### Hardware

- Raspberry Pi 5
- MikroTik RB760iGS Router
- 2x TP-Link TL-SG605E Managed Switches
- Dell OptiPlex 3040
- HP t640 Thin Client
- ESP32 Development Kit
- Desktop Workstation
- Laptop Test Device

### Core Technologies

- Grafana
- Prometheus
- Pi-hole
- Docker
- Docker Compose
- Proxmox VE
- AWS CloudWatch
- MikroTik RouterOS
- Python
- Paramiko

### Network Design

- The lab network is built around a MikroTik RB760iGS router with 2x TP-Link TL-SG605E Managed Switches
- The lab uses "Router on a Stick" (ROAS) with managed L2 switching and VLAN segmentation
- 802.1Q VLAN trunking between managed switches
- Dedicated DHCP scopes per VLAN
- VLAN 10 - Main (trusted devices) 
- VLAN 20 - Isolated (new device onboarding)
- VLAN 30 - Servers
- Automated MikroTik configuration backup to support rollback and recovery of router
- Implemented dedicated management subnet for router and switch configurations

#### Network Security & Hardening

- Restricted WinBox and SSH administrative access to the trusted management VLAN only
- Restricted access from onboarding vlan to management vlan while still preserving DNS, DHCP and internet connectivity
- Enforced inter-vlan isolation using MikroTik firewall filtering rules
- Hardened management-plane exposure by restricting MikroTik Neighbor Discovery and MAC-based management services
- Disabled unnecessary legacy management services including Telnet and FTP
- Maintained isolated lab environment separated from the primary home network infrastructure

#### Network Goals

- Separate trusted infrastructure from newly onboarded and testing devices
- Reduce risk when onboarding used or untrusted hardware into the lab
- Simulate enterprise-style network segmentation
- Support future virtualisation and security tooling
- Maintain operational stability of both home network and lab network during staged infrastructure changes

#### Operational Approach

- Implement changes to lab network using a staged deployment methodology to minimise potential disruptions
- Maintain rollback capability with configuration backups before major infrastructure changes
- Ensure management recovery paths always remain available during testing and troubleshooting
- Validate network segmentation and firewall policy using endpoint testing before wider deployment
- Maintain a dedicated onboarding network for isolated device testing and validation

#### Validation & Testing

- Validated DHCP scope assignment and internet connectivity across segmented VLAN infrastructure
- Confirmed inter-switch 802.1Q VLAN propagation across managed switch trunk links
- Performed endpoint isolation testing between trusted and onboarding VLANs
- Validated firewall policy enforcement through staged reachability and management access testing
- Confirmed onboarding VLAN devices retained DNS, DHCP and internet access while management-plane access remained restricted
- Tested management recovery procedures and rollback workflows before applying major infrastructure changes
- Verified automated MikroTik configuration backup scheduling, export generation and local backup retention workflows

---

### Monitoring & Observability

The lab includes a dedicated observability platform running on a Debian virtual machine hosted on Proxmox VE.

#### Observability Stack

- Prometheus
- Grafana
- Node Exporter
- cAdvisor

#### Monitoring Coverage

##### Proxmox Host

- CPU utilisation
- Memory utilisation
- Disk utilisation
- Network throughput
- System uptime
- System load

##### Virtual Machines

- debian-monitoring-01
- ubuntu-docker-01

Metrics collected:

- CPU utilisation
- Memory utilisation
- Disk utilisation
- Network throughput
- System uptime
- System load

##### Containers

Container-level monitoring is provided through cAdvisor.

Metrics collected:

- Container CPU utilisation
- Container memory utilisation
- Container status and availability

##### Grafana Dashboards

- Homelab Overview
- proxmox01 Dashboard
- debian-monitoring-01 Dashboard
- ubuntu-docker-01 Dashboard
- Container Monitoring Dashboard

### Dashboard Screenshots

#### Homelab Overview
![Homelab Overview](docs/diagrams/homelab-overview-dashboard.JPG)

#### Container Monitoring
![Container Monitoring](docs/diagrams/container-monitoring-dashboard.JPG)

#### Proxmox Host Monitoring
![Proxmox Dashboard](docs/diagrams/proxmox01-dashboard.JPG)

---

### Virtualisation Platform

The lab uses Proxmox VE as the primary virtualisation platform running on a Dell OptiPlex 3040.

#### Current Virtual Machines

##### proxmox01

- Proxmox VE hypervisor
- Hosts all virtualised lab workloads
- Monitored using Prometheus, Grafana and Node Exporter

##### debian-monitoring-01

Dedicated observability platform providing:

- Grafana
- Prometheus
- Node Exporter
- cAdvisor

##### ubuntu-docker-01

Docker workload host providing:

- Docker Engine
- Docker Compose
- Containerised application deployment
- Container-level monitoring via cAdvisor

---

## Project Goals

- Build a VLAN-segmented hybrid infrastructure lab
- Develop networking and infrastructure skills
- Implement monitoring and observability
- Learn and practice virtualisation and Linux administration
- Integrate cloud services with on-premises infrastructure
- Document deployment, troubleshooting and operational workflows


---

## Planned Architecture

- [X] MikroTik core routing
- [X] Managed switch uplinks and trunking
- [X] VLAN segmentation
- [X] Monitoring and observability platform
- [X] Proxmox virtualisation platform
- [ ] Wireless Infrastructure Deployment
- [ ] AWS-integrated hybrid services
- [ ] Windows Server Active Directory

---
## Architecture Diagrams

### Current VLAN Segmented Topology (V2)

![VLAN Segmented Topology V2](docs/diagrams/vlan-segmented-topology-v2.JPG)

Additional deployment diagrams:

- [VLAN Segmented Topology V1](docs/diagrams/vlan-segmented-topology.PNG)
- [Initial MikroTik Deployment](docs/diagrams/initial-mikrotik-deployment.png)  
- [Managed Switch Deployment](docs/diagrams/managed-switch-deployment.png)

## Deployment Strategy

Use a staged rollout approach to:  

- Minimise disruption to the existing home network  
- Validate configurations incrementally  
- Maintain operational stability  
- Support isolated testing and troubleshooting  
- Simulate real-world infrastructure deployment practices

---

## Current Status

### Completed
- [X] Hardware acquisition
- [X] Initial planning and design
- [X] MikroTik setup & deployment (updated RouterOS, created config backups, confirmed network connectivity with test client)
- [X] Architecture diagram creation
- [X] Managed switch deployment (updated firmware, created config backups, confirmed network connectivity with test client)
- [X] Physical network topology implementation
- [X] VLAN design and implementation
- [X] Implement Python script to automatically back up MikroTik configuration using SSH and RouterOS exports
- [X] Configure automated scheduled backups using python script with added timestamps to locally saved file
- [X] Managed switch trunk link configuration and validation
- [X] Managed switch VLAN propagation and endpoint testing
- [X] Secure onboarding of used hardware (Dell OptiPlex 3040)
- [X] Proxmox virtualisation platform deployment
- [X] Ubuntu Server VM deployment
- [X] VLAN design refactoring and implementation
- [X] Proxmox host migration from onboarding VLAN to server VLAN
- [X] Ubuntu Server VM migration from onboarding VLAN to server VLAN
- [X] Desktop-based administration restored from trusted management VLAN
- [X] Debian VM deployment
- [X] Proxmox host monitoring implementation
- [X] Container monitoring implementation using cAdvisor
  
### In Progress
- [ ] Windows Server Active Directory lab

### Planned
- Wireless infrastructure deployment (MikroTik cAP ac)
- Raspberry Pi integration
- AWS CloudWatch implementation
- Centralised device log collection 
- Automated device configuration backups
- Secure onboarding of used hardware (HP t640 Thin Client)
- Security monitoring

---

## Issues & Troubleshooting

- Diagnosed and resolved MikroTik VLAN deployment issue where DNS and management traffic were being blocked by firewall interface-list behaviour
- Resolved temporary management lockout during VLAN migration by using direct recovery access
- Identified and corrected legacy switch management addressing remaining from pre-VLAN deployment
- Diagnosed inter-vlan management reachability behaviour and implemented MikroTik firewall filter rules to enforce onboarding VLAN isolation
- Identified that MikroTik MAC-based management and Neighbor Discovery services could bypass Layer 3 firewall isolation during Onboarding VLAN testing  
- Investigated management-plane exposure by validating inter-VLAN firewall behaviour, service accessibility and discovery protocols across segmented VLAN infrastructure  
- Implemented dedicated management interface list and restricted WinBox, SSH, MAC Server and Neighbor Discovery access to the trusted management VLAN only  
- Successfully hardened Onboarding VLAN isolation while preserving DHCP, DNS and internet connectivity for untrusted devices
- Diagnosed VLAN30 connectivity failure caused by SW02 Port 4 retaining its VLAN20 PVID after being reassigned as an untagged VLAN30 access port
- Updated Proxmox host network configuration after identifying that the host retained its VLAN20 addressing following migration to the VLAN30 server network
- Reconfigured Ubuntu Server VM networking after identifying that the VM retained its previous VLAN20 DHCP lease after the Proxmox bridge moved to VLAN30
- Diagnosed inter-VLAN firewall rule ordering issue where VLAN30 return traffic to VLAN10 was dropped before established and related traffic was accepted
- Distinguished MikroTik input-chain gateway traffic from forward-chain inter-VLAN host traffic during firewall validation and rule placement
- Identified local Windows firewall behaviour as the cause of VLAN20 laptop ICMP reachability issues after validating MikroTik routing, VLAN tagging and firewall policy

## Related Projects

- [raspberry-pi-system-monitor](https://github.com/Am1tp/raspberry-pi-system-monitor)
- [pihole-infrastructure](https://github.com/Am1tp/pihole-infrastructure)

