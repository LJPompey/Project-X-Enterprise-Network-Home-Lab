<div align="center">

# 🛡️ Project X: Enterprise Network Simulation & Threat Hunting
### End-to-End AD Infrastructure, SIEM Deployment, and Incident Response

This repository documents the architecture and execution of a fully virtualized, segmented corporate network. The project encompasses the entire Cyber Kill Chain, from provisioning Active Directory and deploying a centralized security stack (Wazuh & Security Onion) to executing simulated cyberattacks (Kali Linux) and conducting live incident response.

[Read the Full Technical Breakdown on Medium](https://medium.com/@pompey.lamont01/architecting-project-x-end-to-end-enterprise-network-simulation-threat-hunting-d575b86c3d24)

</div>

---

## 🏗️ Core Architecture & Topology
The environment was engineered entirely within **VMware Workstation Pro**, utilizing custom NAT networking to isolate the lab environment from the physical host.

*   **Domain Controller:** Windows Server 2025 (Active Directory, DNS, Centralized Authentication)
*   **Corporate Endpoints:** Windows 11 Enterprise & Ubuntu Desktop 22.04
*   **Internal Services:** Ubuntu Server hosting MailHog (Simulated internal email traffic)
*   **Security Stack:** Dedicated Ubuntu 22.04 server hosting **Wazuh** (SIEM/XDR) and **Security Onion**
*   **Attacker Machine:** Kali Linux

## ✨ Project Lifecycle & Features

### 1. Infrastructure & Identity Management
*   Provisioned a Windows Server Domain Controller to establish a forest root domain.
*   Configured Organizational Units (OUs) and Role-Based Access Control (RBAC) to simulate a realistic corporate hierarchy.
*   Joined hybrid endpoints (Windows 11 and Ubuntu) to the domain to centralize authentication and security policies.

### 2. Security Deployment & Baseline
*   Deployed a centralized Wazuh SIEM to monitor endpoint telemetry and network traffic.
*   Engineered custom detection rules and alerts within Wazuh to establish a baseline of normal network behavior prior to the red team engagement.

### 3. Red Team Operations (Offensive Security)
*   Executed a systematic compromise of the network utilizing Kali Linux.
*   **Reconnaissance & Initial Access:** Mapped network vulnerabilities to establish an initial foothold.
*   **Privilege Escalation:** Navigated the internal network laterally to compromise higher-value administrative targets.
*   **Persistence & Exfiltration:** Simulated data theft and established backdoor access for continued control.

### 4. Blue Team Defense (Incident Response)
*   Pivoted to a defensive posture, utilizing the Wazuh dashboard and Security Onion to hunt for the established threat footprint.
*   Correlated alerts to map the exact timestamps and TTPs (Tactics, Techniques, and Procedures) of the simulated breach, validating the efficacy of the custom detection rules.

---

## 🛠️ Tech Stack
*   **Hypervisor:** VMware Workstation Pro
*   **Identity & Access Management:** Microsoft Active Directory (AD DS)
*   **SIEM & Network Security:** Wazuh, Security Onion
*   **Offensive Tools:** Kali Linux (NetExec, Hydra, Evil-WinRM)
*   **Operating Systems:** Windows Server, Windows 11, Ubuntu 22.04

---

*Note: This project is adapted from Grant Collins' excellent [Project Security] (https://projectsecurity.teachable.com/l/dashboard) curriculum, modified by me to utilize VMware Workstation Pro for enhanced hypervisor isolation and performance.*
