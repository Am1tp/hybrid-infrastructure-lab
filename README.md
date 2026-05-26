# hybrid-infrastructure-lab

## Overview

A self-hosted enterprise-style hybrid lab designed to develop practical skills in networking, observability, Linux administration, virtualisation and cloud-integrated operations.

This project aims to develop practical hands-on experience in:

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

### Technologies

- Grafana
- Prometheus
- Pi-hole
- Docker
- Docker Compose
- Proxmox VE
- AWS CloudWatch
- MikroTik RouterOS


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

- MikroTik core routing
- Managed switch uplinks and trunking
- VLAN segmentation
- Monitoring and observability platform
- Proxmox virtualisation platform
- AWS-integrated hybrid services

---
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
- Hardware acquisition
- Initial planning and design
- MikroTik setup & deployment (updated RouterOS, created config backups, confirmed network connectivity with test client)
  
### In Progress
- Architecture diagram creation
- Managed switch deployment
- Physical network topology implementation
  
### Planned
- Managed switch deployment
- VLAN design and implementation
- Secure onboarding of used hardware (Dell OptiPlex 3040, HP t640 Thin Client)
- Raspberry Pi integration
- Monitoring and observability implementation
- AWS CloudWatch implementation
- Proxmox virtualisation platform deployment
- Linux virtual machine deployment
- Centralised device log collection 
- Automated device configuration backups
- ESP32 experimentation

---

## Related Projects

- raspberry-pi-system-monitor
- pihole-infrastructure

