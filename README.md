# 🏭 Manufacturing ERP: Azure Cloud Migration & Disaster Recovery

![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=for-the-badge&logo=microsoftazure&logoColor=white)
![Windows Server](https://img.shields.io/badge/Windows%20Server-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![SQL Server](https://img.shields.io/badge/SQL%20Server-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)

## 📋 Project Overview
This project demonstrates a complete **Lift & Shift** migration of a legacy Manufacturing ERP system to Microsoft Azure. It features an enterprise-grade **Hub & Spoke network topology**, **Zero Trust security**, and a **Disaster Recovery (DR)** strategy ensuring high availability.

**Primary Region:** Italy North  
**DR Region:** North Europe  

---

## 🏗️ Architecture
The solution uses a **Hub-Spoke topology** to segregate workloads and centralize security.

### High-Level Design
*   **Global Access:** Azure Front Door (WAF enabled) for global load balancing.
*   **Network:** Hub VNet for shared services (Firewall, VPN) peered with 3 isolated Spoke VNets (Database, App, Storage).
*   **Hybrid Connectivity:** Azure Arc for managing on-premises SQL assets.
*   **Disaster Recovery:** Active-Passive setup using Azure Site Recovery (ASR).

### Topology Diagram
![Project Diagram](Project%20Diagram.png)

---

## 🚀 Key Features Implemented

### 1. Advanced Networking & Security
*   **Hub-Spoke Topology:** Centralized traffic inspection via Azure Firewall (Standard SKU).
*   **Zero Trust:** Strict Network Security Groups (NSGs) and User Defined Routes (UDRs) forcing all spoke traffic through the central firewall (10.0.2.4).
*   **Private Connectivity:** Private Endpoints for Azure Storage (Files & Blob) to eliminate public internet exposure.
*   **Secure Remote Access:** Point-to-Site (P2S) VPN Gateway (VpnGw1) for administrative access using OpenVPN.

### 2. Compute & Application
*   **Web Tier:** Windows Server 2022 (B2als_v2) running IIS with Python/Flask via WFastCGI.
*   **Data Tier:** SQL Server 2022 on Azure VM (B2als_v2) isolated in a dedicated database subnet.
*   **Hybrid Management:** Extended Azure management plane to on-prem SQL servers using **Azure Arc**.

### 3. Business Continuity & Disaster Recovery (BCDR)
*   **Compute DR:** **Azure Site Recovery (ASR)** for continuous VM replication (RPO < 15 mins).
*   **Automated Failover:** Validated runbooks for regional failover via Recovery Services Vault.
*   **Global Resilience:** Azure Front Door health probes automatically reroute traffic during regional outages.

---

## 🛠️ Technologies Used
*   **Cloud Platform:** Microsoft Azure
*   **Infrastructure:** Virtual Machines, Virtual Networks, VPN Gateway, Azure Firewall
*   **Load Balancing:** Azure Front Door
*   **Databases:** Azure SQL VM, Azure Arc
*   **Storage:** Azure Files (SMB), Azure Blob Storage
*   **DevOps/Scripting:** PowerShell, Bicep/ARM, Bash

---

## 📝 Deliverables
*   [Scope of Work](./02-Deliverables/01-Scope-of-Work.pdf)
*   [Disaster Recovery Runbook](./02-Deliverables/02-DR-Runbook.pdf)
*   [Network Architecture Design](./02-Deliverables/04-Hub_Spoke_Design.pdf)
*   [Sizing Document](./02-Deliverables/03-Sizing-Document.pdf)
*   [Subnet Segmentation](./02-Deliverables/05-Subnet_Segmentation.pdf)
*   [Phased Project Plan](./02-Deliverables/06-Phased%20Project%20Plan.xlsx)

---

