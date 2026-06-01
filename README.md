# 👁️ ShadowSentry

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version: v1.0](https://img.shields.io/badge/Version-v1.0-blue.svg)](https://github.com/transparency-x/shadowsentry/releases)
[![Python 3.11+](https://img.shields.io/badge/Python-3.11+-green.svg)](https://www.python.org/downloads/)
[![Docker](https://img.shields.io/badge/Docker-Ready-2496ED.svg)](https://www.docker.com/)

**ShadowSentry** is a modular, open-source framework for deploying **secure, anonymous surveillance systems** at any scale. Whether you're monitoring a single remote camera or coordinating a global network, ShadowSentry provides the tools to **encrypt, obfuscate, and scale** your operations while minimizing detection risks.

---

## ✨ Features

| **Category**          | **Feature**                          | **Free/Open Source** | **Low Cost**       | **Mid Cost**          | **High Cost**               |
|-----------------------|--------------------------------------|----------------------|--------------------|------------------------|-----------------------------|
| **Encryption**        | End-to-end (E2EE) for data in transit | ✅ (Signal Protocol) | ✅ (WireGuard)     | ✅ (IPSec)             | ✅ (LibreSignal + MPC)      |
| **Encryption**        | Local storage encryption             | ✅ (AES-256)         | ✅ (LUKS)          | ✅ (ZFS Encryption)   | ✅ (Hardware HSM)           |
| **IP Masking**        | Static IP obfuscation                | ✅ (TOR)             | ✅ (Residential Proxies) | ✅ (Anycast Routing) | ✅ (BGP Anycast + ASN Rotation) |
| **IP Masking**        | Dynamic IP rotation                  | ✅ (SOCKS5)          | ✅ (Luminati)      | ✅ (Oxylabs)           | ✅ (Custom CDN Fronting)    |
| **Proxies**           | Basic proxy support                  | ✅ (Squid)           | ✅ (HAProxy)        | ✅ (Nginx + Geo-IP)   | ✅ (Cloudflare Enterprise) |
| **Proxies**           | Load balancing                       | ❌                  | ✅ (HAProxy)        | ✅ (Nginx Plus)        | ✅ (F5 BIG-IP)              |
| **VPNs**             | Device-level VPN                     | ✅ (OpenVPN)         | ✅ (WireGuard)     | ✅ (Tailscale)         | ✅ (Nebula + ZeroTier)      |
| **VPNs**             | Site-to-site VPN                     | ✅ (OpenVPN)         | ✅ (WireGuard)     | ✅ (IPSec)             | ✅ (Cisco AnyConnect)       |
| **Isolated Browsers**| Browser isolation                    | ✅ (Firefox Containers) | ✅ (Brave + TOR) | ✅ (Qubes OS)          | ✅ (Air-Gapped Workstations) |
| **Isolated Browsers**| Anti-fingerprinting                  | ✅ (Privacy Badger) | ✅ (Multilogin)     | ✅ (GoLogin)           | ✅ (Custom VM Snapshots)    |
| **Network**          | VLAN segmentation                     | ❌                  | ✅ (pfSense)        | ✅ (Cisco Switches)   | ✅ (Juniper QFX)             |
| **Network**          | Traffic shaping                      | ❌                  | ✅ (tc/iptables)   | ✅ (Cisco QoS)        | ✅ (SolarWinds)             |
| **Storage**          | Encrypted cloud storage              | ✅ (Cryptomator)     | ✅ (Backblaze B2)  | ✅ (AWS S3 + KMS)     | ✅ (Private S3-Compatible)   |
| **Storage**          | Decentralized storage                | ✅ (IPFS)            | ✅ (Storj)          | ✅ (Filecoin)          | ✅ (Custom Blockchain)      |
| **Monitoring**       | Log analysis                          | ✅ (ELK Stack)       | ✅ (Grafana)        | ✅ (Splunk)            | ✅ (Elastic SIEM)            |
| **Automation**       | Deployment automation                | ✅ (Ansible)         | ✅ (Terraform)      | ✅ (Kubernetes)       | ✅ (HashiCorp Nomad)        |

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11+
- Docker (for containerized deployments)
- Git

### Installation
```bash
# Clone the repository
git clone https://github.com/transparency-x/shadowsentry.git
cd shadowsentry

# Install dependencies
pip install -r requirements.txt

# Run the setup script
python setup.py
```

### Quick Deploy (Docker)
```bash
# Build and run the container
docker-compose up --build
```

---

## 📂 Project Structure
```
shadowsentry/
├── docs/                  # Documentation and guides
│   ├── single-unit.md     # Single camera/mic setup
│   ├── lan.md             # Local Area Network setup
│   ├── county-wide.md     # County-wide deployment
│   └── global.md          # Multi-network/Global setup
├── scripts/               # Automation scripts (Ansible, Terraform)
├── configs/               # Pre-configured templates for VPNs, proxies, etc.
├── src/                   # Core modules (encryption, IP rotation, etc.)
└── README.md              # This file
```

---

## 🛠️ Configuration

### Single Unit Example (Camera + Mic)
```yaml
# config/single-unit.yml
device:
  name: "remote-cam-01"
  type: "camera"
  encryption:
    local: "AES-256"
    transit: "WireGuard"
  ip_masking:
    method: "TOR"
    proxy: "SOCKS5"
  vpn:
    provider: "Mullvad"
    protocol: "WireGuard"
```

### LAN Example (Office/Building)
```yaml
# config/lan.yml
network:
  name: "office-surveillance"
  vlan_id: 10
  gateway: "pfSense"
  vpn:
    type: "site-to-site"
    protocol: "OpenVPN"
  proxies:
    - "HAProxy"
    - "Squid"
  ip_rotation: true
```

---

## 📊 Cost Tiers

| **Tier**       | **Description**                                                                 | **Estimated Monthly Cost** | **Best For**                     |
|----------------|---------------------------------------------------------------------------------|----------------------------|----------------------------------|
| **Free**       | Open-source tools, self-hosted, community proxies/VPNs                         | $0                         | Testing, small-scale, hobbyists  |
| **Low Cost**   | Affordable commercial proxies/VPNs, basic cloud storage                         | $50–$200                   | Small teams, local deployments   |
| **Mid Cost**   | Enterprise-grade proxies, redundant VPNs, encrypted cloud storage              | $200–$1,000                | County-wide, professional use    |
| **High Cost**  | Custom infrastructure, BGP anycast, hardware HSMs, air-gapped workstations     | $1,000+                     | Global, high-security needs      |

---

## 🤝 Contributing
Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

---

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

---

## **🎯 Roadmap**

### **v1.0 (Current – June 2026)**
| **Feature**                          | **Status**  | **Free** | **Low Cost** | **Mid Cost** | **High Cost** | **Notes**                                  |
|--------------------------------------|-------------|----------|--------------|--------------|---------------|--------------------------------------------|
| Basic E2EE (Signal Protocol)         | ✅ Complete | ✅        | ✅            | ✅            | ✅             | Works for single units and LANs.          |
| TOR + SOCKS5 IP Masking              | ✅ Complete | ✅        | ✅            | ✅            | ✅             | Basic obfuscation for all tiers.          |
| OpenVPN/WireGuard Support            | ✅ Complete | ✅        | ✅            | ✅            | ✅             | Device and site-to-site VPNs.             |
| Firefox Containers for Isolation     | ✅ Complete | ✅        | ✅            | ✅            | ❌             | Limited to browser-level isolation.       |
| pfSense VLAN Templates               | ✅ Complete | ❌        | ✅            | ✅            | ✅             | Pre-configured for LAN deployments.       |
| Ansible Deployment Scripts           | ✅ Complete | ✅        | ✅            | ✅            | ✅             | Automates setup for all tiers.            |

---

### **v1.1 (Q3 2026)**
| **Feature**                          | **Status**  | **Free** | **Low Cost** | **Mid Cost** | **High Cost** | **Notes**                                  |
|--------------------------------------|-------------|----------|--------------|--------------|---------------|--------------------------------------------|
| **IPSec Support**                    | 🚧 Planned  | ✅        | ✅            | ✅            | ✅             | For site-to-site encryption.              |
| **Residential Proxy Integration**    | 🚧 Planned  | ❌        | ✅            | ✅            | ✅             | Luminati/Oxylabs for IP rotation.          |
| **HAProxy Load Balancing**           | 🚧 Planned  | ❌        | ✅            | ✅            | ✅             | Distributes traffic across proxies.       |
| **Qubes OS Templates**               | 🚧 Planned  | ❌        | ❌            | ✅            | ✅             | For isolated browser environments.        |
| **ZFS Encrypted Storage**            | 🚧 Planned  | ❌        | ❌            | ✅            | ✅             | Local encrypted storage.                  |
| **Terraform Cloud Templates**        | 🚧 Planned  | ✅        | ✅            | ✅            | ✅             | Infrastructure-as-code for cloud setups.  |

---

### **v1.2 (Q4 2026)**
| **Feature**                          | **Status**  | **Free** | **Low Cost** | **Mid Cost** | **High Cost** | **Notes**                                  |
|--------------------------------------|-------------|----------|--------------|--------------|---------------|--------------------------------------------|
| **Anycast Routing**                  | 🚧 Planned  | ❌        | ❌            | ✅            | ✅             | For county-wide IP masking.                |
| **BGP Anycast + ASN Rotation**       | 🚧 Planned  | ❌        | ❌            | ❌            | ✅             | Global-scale obfuscation.                 |
| **Tailscale/Nebula Mesh VPNs**        | 🚧 Planned  | ✅        | ✅            | ✅            | ✅             | Peer-to-peer VPN for distributed networks.|
| **Storj/Filecoin Storage**           | 🚧 Planned  | ✅        | ✅            | ✅            | ✅             | Decentralized encrypted storage.          |
| **Grafana Dashboards**               | 🚧 Planned  | ✅        | ✅            | ✅            | ✅             | Monitoring and analytics.                 |

---

### **v2.0 (2027)**
| **Feature**                          | **Status**  | **Free** | **Low Cost** | **Mid Cost** | **High Cost** | **Notes**                                  |
|--------------------------------------|-------------|----------|--------------|--------------|---------------|--------------------------------------------|
| **AI-Powered Traffic Obfuscation**  | 📅 Roadmap  | ❌        | ❌            | ✅            | ✅             | Dynamically adjusts to avoid detection.   |
| **Hardware HSM Support**              | 📅 Roadmap  | ❌        | ❌            | ❌            | ✅             | For high-security encryption.             |
| **Blockchain Key Management**        | 📅 Roadmap  | ❌        | ❌            | ❌            | ✅             | Decentralized access control.             |
| **Multi-Party Computation (MPC)**    | 📅 Roadmap  | ❌        | ❌            | ❌            | ✅             | Requires 2-of-3 signatures for access.    |
| **Custom CDN Fronting**               | 📅 Roadmap  | ❌        | ❌            | ❌            | ✅             | Blends traffic with legitimate CDN users. |
| **Air-Gapped Workstations**          | 📅 Roadmap  | ❌        | ❌            | ❌            | ✅             | For maximum isolation.                    |

---

## **📋 v1.0 Report: Deployment Scenarios**

### **1️⃣ Single Unit (Remote Camera/Microphone)**

| **Component**         | **Free/Open Source**               | **Low Cost**                     | **Mid Cost**                     | **High Cost**                     |
|-----------------------|------------------------------------|----------------------------------|----------------------------------|------------------------------------|
| **Device**            | Raspberry Pi + Camera Module        | Reolink/Eufy Camera              | Axis Communications Camera      | FLIR Thermal Camera               |
| **Encryption**        | AES-256 (OpenSSL)                  | WireGuard VPN                   | IPSec VPN                        | Hardware HSM (YubiHSM)             |
| **IP Masking**        | TOR                                | Residential Proxy (Luminati)    | Anycast Proxy (Cloudflare)       | BGP Anycast + ASN Rotation         |
| **Proxy**             | SOCKS5 (Dante)                     | HAProxy                          | Nginx + Geo-IP                   | F5 BIG-IP                          |
| **VPN**               | OpenVPN                            | Mullvad VPN                      | Tailscale                        | Nebula + ZeroTier                 |
| **Isolated Browser** | Firefox Containers                 | Brave + TOR                      | Qubes OS                         | Air-Gapped Workstation            |
| **Storage**           | Local (LUKS Encryption)            | Backblaze B2 (Cryptomator)       | AWS S3 (KMS)                     | Private S3-Compatible (MinIO)      |
| **Automation**        | Bash Scripts                       | Ansible                          | Terraform                        | HashiCorp Nomad                   |
| **Monitoring**        | Netdata                            | Grafana Cloud                    | Splunk                           | Elastic SIEM                       |
| **Estimated Cost**    | **$0–$50**                          | **$50–$200/month**               | **$200–$1,000/month**            | **$1,000+/month**                 |
| **Use Case**          | Personal, testing, small projects | Small teams, local businesses    | Corporate, county-wide            | Government, global operations      |

---

### **2️⃣ Local Area Network (LAN: Office/Building)**

| **Component**         | **Free/Open Source**               | **Low Cost**                     | **Mid Cost**                     | **High Cost**                     |
|-----------------------|------------------------------------|----------------------------------|----------------------------------|------------------------------------|
| **Network Hardware** | Consumer Router (OpenWRT)          | Ubiquiti UniFi                   | Cisco Switches                   | Juniper QFX Series                 |
| **Encryption**        | WireGuard Mesh                     | OpenVPN (Gateway)                | IPSec (Site-to-Site)             | Cisco AnyConnect                   |
| **IP Masking**        | TOR + NAT                          | Residential Proxy Pool            | Anycast Routing (Cloudflare)     | Custom CDN Fronting                |
| **Proxy**             | Squid Proxy                        | HAProxy                          | Nginx Plus                        | F5 BIG-IP                          |
| **VPN**               | OpenVPN                            | WireGuard (Gateway)              | Tailscale                        | Nebula + ZeroTier                 |
| **Isolated Browser** | Firefox Containers                 | Brave + TOR                      | Qubes OS                         | Air-Gapped Workstation            |
| **Storage**           | NAS (Synology + AES-256)           | Backblaze B2 (Cryptomator)       | AWS S3 (KMS)                     | Private Ceph Cluster               |
| **Segmentation**      | VLANs (OpenWRT)                    | pfSense Firewall                 | Cisco ASA Firewall               | Palo Alto Networks                 |
| **Automation**        | Ansible                            | Terraform (Cloud)                | Kubernetes                       | HashiCorp Nomad                   |
| **Monitoring**        | ELK Stack                          | Grafana Cloud                    | Splunk                           | Elastic SIEM                       |
| **Estimated Cost**    | **$100–$500**                       | **$500–$2,000/month**            | **$2,000–$10,000/month**          | **$10,000+/month**                 |
| **Use Case**          | Small offices, home labs           | Startups, local businesses       | Corporate campuses, schools      | Enterprise, critical infrastructure |

---

### **3️⃣ County-Wide (Distributed Surveillance)**

| **Component**         | **Free/Open Source**               | **Low Cost**                     | **Mid Cost**                     | **High Cost**                     |
|-----------------------|------------------------------------|----------------------------------|----------------------------------|------------------------------------|
| **Network Topology**  | Peer-to-Peer (ZeroTier)            | Hub-and-Spoke (WireGuard)        | SD-WAN (Cisco Viptela)           | BGP Anycast (Juniper)               |
| **Encryption**        | IPSec (StrongSwan)                 | WireGuard (Site-to-Site)         | Tailscale Mesh                   | LibreSignal + MPC                  |
| **IP Masking**        | TOR Middle Relays                  | Residential Proxy Pool            | Anycast Routing (Cloudflare)     | Custom BGP Anycast                 |
| **Proxy**             | HAProxy                            | Nginx + Geo-IP                   | Cloudflare Enterprise             | F5 BIG-IP                          |
| **VPN**               | OpenVPN                            | WireGuard                        | Tailscale                        | Nebula + ZeroTier                 |
| **Isolated Browser** | Firefox Containers                 | Brave + TOR                      | Qubes OS                         | Air-Gapped Workstations            |
| **Storage**           | IPFS + Filecoin                    | Storj + Cryptomator              | AWS S3 (KMS) + Glacier            | Private Distributed Storage        |
| **Redundancy**        | Failover Scripts                   | HAProxy + Keepalived              | Kubernetes (Multi-Region)        | VMware NSX                         |
| **Automation**        | Ansible                            | Terraform                        | Kubernetes                       | HashiCorp Nomad + Consul           |
| **Monitoring**        | Prometheus + Grafana               | Grafana Cloud                    | Splunk                           | Elastic SIEM + Darktrace           |
| **Estimated Cost**    | **$1,000–$5,000/month**             | **$5,000–$20,000/month**          | **$20,000–$100,000/month**        | **$100,000+/month**                |
| **Use Case**          | Community projects, research       | County security, mid-sized orgs  | Municipal surveillance, ISPs     | National infrastructure, military |

---

### **4️⃣ Multi-Network/Global (Merged Networks)**

| **Component**         | **Free/Open Source**               | **Low Cost**                     | **Mid Cost**                     | **High Cost**                     |
|-----------------------|------------------------------------|----------------------------------|----------------------------------|------------------------------------|
| **Network Topology**  | Nebula Mesh                        | Tailscale                        | ZeroTier + SD-WAN                | BGP Anycast (Juniper MX)           |
| **Encryption**        | LibreSignal                        | WireGuard (Multi-Region)         | IPSec (Cisco ASA)                 | Hardware HSM (Thales)              |
| **IP Masking**        | TOR + CDN Fronting                 | Residential Proxy Pool            | Anycast (Cloudflare Enterprise)  | Custom BGP Anycast + ASN Rotation  |
| **Proxy**             | Squid + HAProxy                    | Nginx + Geo-IP                   | Cloudflare Enterprise             | F5 BIG-IP + Akamai                 |
| **VPN**               | OpenVPN                            | WireGuard                        | Tailscale                        | Nebula + ZeroTier + Cisco AnyConnect |
| **Isolated Browser** | Whonix VM                          | Multilogin                        | GoLogin                           | Air-Gapped + Custom VM Snapshots    |
| **Storage**           | IPFS + Storj                       | Backblaze B2 + Cryptomator       | AWS S3 (KMS) + Glacier            | Private Blockchain Storage         |
| **Redundancy**        | Multi-Path Routing (BIRD)          | HAProxy + Keepalived              | Kubernetes (Multi-Cloud)         | VMware NSX + Cisco ACI              |
| **Automation**        | Ansible + Terraform                | Terraform Cloud                  | Kubernetes + ArgoCD               | HashiCorp Nomad + Consul + Vault   |
| **Monitoring**        | ELK Stack                          | Grafana Cloud                    | Splunk + Darktrace                | Elastic SIEM + Chronicle           |
| **Legal Obfuscation**| Shell Companies (DIY)              | Privacy-Friendly Jurisdictions   | Offshore Entities                 | Multi-Jurisdictional Shell Cos.    |
| **Estimated Cost**    | **$5,000–$20,000/month**            | **$20,000–$100,000/month**        | **$100,000–$500,000/month**       | **$500,000+/month**                |
| **Use Case**          | Research, activism                  | Global NGOs, corporations         | Multi-national orgs              | Governments, intelligence agencies |

---

## **🔍 Risk Assessment by Scale**

| **Risk**                          | **Single Unit** | **LAN**       | **County-Wide** | **Multi-Network** | **Mitigation**                                                                                     |
|-----------------------------------|-----------------|---------------|-----------------|-------------------|----------------------------------------------------------------------------------------------------|
| **IP Leaks**                      | High            | Medium        | Low              | Very Low          | Use **kill switches**, **leak protection**, and **multi-layer obfuscation**.                       |
| **Traffic Analysis**              | Medium          | High          | Very High       | Extreme           | **Traffic shaping**, **protocol obfuscation**, and **randomized patterns**.                          |
| **Device Compromise**             | High            | Medium        | Low              | Very Low          | **Hardware isolation**, **air-gapped controls**, and **regular audits**.                              |
| **Legal Exposure**                | Low             | Medium        | High            | Extreme           | **Jurisdictional arbitrage**, **shell companies**, and **plausible deniability**.                     |
| **Cost Overruns**                 | Low             | Medium        | High            | Very High         | **Modular scaling**, **cost-tiered options**, and **automated failover**.                            |
| **Single Point of Failure**       | Medium          | High          | Medium          | Low               | **Redundant gateways**, **multi-path routing**, and **decentralized storage**.                       |

---

## **💡 Recommendations by Use Case**

| **Use Case**               | **Recommended Tier** | **Key Technologies**                                                                 | **Estimated Budget**       |
|----------------------------|----------------------|--------------------------------------------------------------------------------------|----------------------------|
| **Personal Security**      | Free/Low Cost        | TOR, WireGuard, Firefox Containers, Raspberry Pi                                    | $0–$200/month              |
| **Small Business**         | Low Cost             | HAProxy, Residential Proxies, pfSense, Ubiquiti UniFi                               | $200–$1,000/month          |
| **Corporate Surveillance**| Mid Cost             | Tailscale, Anycast Routing, Qubes OS, AWS S3 (KMS)                                   | $1,000–$10,000/month       |
| **Municipal/County**       | Mid/High Cost        | SD-WAN, Cloudflare Enterprise, Kubernetes, Splunk                                   | $10,000–$100,000/month     |
| **Global Operations**      | High Cost            | BGP Anycast, Hardware HSMs, Air-Gapped Workstations, Multi-Jurisdictional Shell Cos. | $100,000+/month            |

---

## **📅 Next Steps for Transparency-X**

| **Priority** | **Action Item**                                                                 | **Owner**   | **Timeline**       | **Dependencies**                          |
|--------------|---------------------------------------------------------------------------------|-------------|--------------------|------------------------------------------|
| High         | Deploy **v1.0** for single-unit testing (Raspberry Pi + TOR + WireGuard)       | Declan      | June–July 2026     | Hardware procurement, VPN setup         |
| High         | Set up **LAN template** for office surveillance (pfSense + HAProxy)            | Team        | July–August 2026   | Network segmentation, proxy configuration |
| Medium       | Integrate **residential proxies** (Luminati/Oxylabs) for IP rotation             | Team        | August–September 2026 | Budget approval, proxy provider setup   |
| Medium       | Develop **Ansible/Terraform scripts** for automated deployments                 | Dev Team    | September–October 2026 | Testing, documentation                   |
| Low          | Explore **BGP Anycast** for county-wide obfuscation                              | Declan      | Q4 2026            | ISP partnerships, legal review          |
| Low          | Research **Hardware HSMs** and **MPC** for high-security use cases               | Security Team | Q1 2027         | Vendor evaluation, budget approval      |

---

## **🔗 Resources**

| **Category**          | **Resource**                                                                 | **Link**                                                                                     |
|-----------------------|------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| **Documentation**     | ShadowSentry Wiki                                                          | [Link to Wiki](https://github.com/transparency-x/shadowsentry/wiki)                         |
| **Community**         | GitHub Discussions                                                         | [Link](https://github.com/transparency-x/shadowsentry/discussions)                          |
| **Support**           | Transparency-X Slack                                                      | [Invite Link](https://join.slack.com/t/transparency-x/shared_invite/...)                   |
| **Free Tools**        | TOR Project                                                                | [https://www.torproject.org](https://www.torproject.org)                                   |
| **Free Tools**        | WireGuard                                                                 | [https://www.wireguard.com](https://www.wireguard.com)                                       |
| **Low-Cost Proxies**  | Luminati (Now BrightData)                                                 | [https://brightdata.com](https://brightdata.com)                                             |
| **Mid-Cost Proxies**  | Oxylabs                                                                   | [https://oxylabs.io](https://oxylabs.io)                                                     |
| **High-Cost Proxies** | Cloudflare Enterprise                                                     | [https://www.cloudflare.com/enterprise](https://www.cloudflare.com/enterprise)               |
| **VPNs**              | Mullvad                                                                   | [https://mullvad.net](https://mullvad.net)                                                   |
| **Isolation**         | Qubes OS                                                                  | [https://qubes-os.org](https://qubes-os.org)                                                 |
