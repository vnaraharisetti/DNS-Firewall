# Home Network DNS Firewall with AdGuard Home

[![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-Zero%202W%20(64--bit)-C51A4A.svg)](https://www.raspberrypi.com/)
[![AdGuard Home](https://img.shields.io/badge/AdGuard%20Home-v0.107.43-green.svg)](https://github.com/AdguardTeam/AdGuardHome)
[![OS](https://img.shields.io/badge/OS-Raspberry%20Pi%20OS%20Bookworm%20Lite-blue.svg)](https://www.raspberrypi.com/software/)
[![License](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

**A privacy-focused, network-level DNS firewall that blocks ads, trackers, and malicious domains for all devices on your home network.**

## 🛡️ Overview

This project implements a comprehensive DNS-based firewall using AdGuard Home running on a Raspberry Pi Zero 2W. It operates at the network level to block advertisements, tracking scripts, phishing attempts, and malicious domains before they reach any device on your network. By filtering DNS requests in real-time, it enhances privacy, reduces data theft risks, and provides granular control over network traffic.

## ✨ Features

- **Network-wide Protection**: All devices benefit automatically - no per-device configuration needed
- **Ad & Tracker Blocking**: Blocks advertisements and tracking scripts across websites and apps
- **Privacy Enhancement**: Prevents data collection by third-party trackers
- **Security Layer**: Blocks known phishing and malware domains
- **Real-time Analytics**: Dashboard showing DNS queries, blocked requests, and traffic patterns
- **Custom Filter Rules**: Add/remove domains from blocklists as needed
- **Low-power Operation**: Runs 24/7 on energy-efficient Raspberry Pi Zero 2W
- **IPv4/IPv6 Support**: Full dual-stack network compatibility
- **DoH/DoT Support**: DNS-over-HTTPS and DNS-over-TLS capabilities

## 📊 Architecture
[All Network Devices]
↓
[Home Router/Gateway] → DNS Settings Point to → [Raspberry Pi Zero 2W]
↓ ↓
[Internet] [AdGuard Home DNS Filter]
↓ ↓
[Allowed Requests] [Blocked Requests]
↓ ↓
[Upstream DNS] [Local Block]

## 🛠️ Hardware & Software Stack

### **Hardware:**
- **Raspberry Pi Zero 2W** (64-bit ARM Cortex-A53, 512MB RAM)
- MicroSD Card (16GB+ recommended)
- Micro-USB power supply
- Ethernet or Wi-Fi connectivity

### **Software:**
- **Operating System**: Raspberry Pi OS Lite (Bookworm, 64-bit)- write using Raspberry Pi imager
- **Core Application**: AdGuard Home v0.107.43 (open-source)
- **Network Management**: systemd-networkd / NetworkManager
- **Filter Lists**: Combination of AdGuard DNS filter, OISD, StevenBlack hosts, and custom rules

## 📈 Dashboard & Monitoring

AdGuard Home provides a comprehensive web dashboard showing:
- Real-time DNS query statistics
- Blocked requests count and percentage
- Top domains and clients
- Query types and response times
- Historical data with time-based filtering

[dashboard screenshots]

## 🚀 Installation & Configuration

### **1. Hardware Setup**
```bash
# Flash Raspberry Pi OS Lite (64-bit) bookworm to microSD card using Raspberry Pi Imager
# Configure Wi-Fi/Ethernet and enable SSH
# Boot Raspberry Pi Zero 2W
# provide a static IP address for Raspberry Pi 

```
### **2. AdGuard Home Installation**
```bash
# use ssh to connect to pi: ssh username@pi -ip address
# ssh-PI:
# Download and install AdGuard Home
curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v

# Start AdGuard Home service
sudo systemctl start AdGuardHome
sudo systemctl enable AdGuardHome

# From any device on the network:
# Access setup wizard at http://<raspberry-pi-ip>:3000

```
### **3.Network Configuration**
```bash
# ssh-PI:
# Configure AdGuard Home to listen on port 53 (DNS)
# Set upstream DNS servers (Cloudflare, Quad9, or your ISP)

# On your router:
# 1. Navigate to DNS settings
# 2. Set the primary DNS to your Raspberry Pi's IP address
# 3. Save and reboot the router if necessary

```
### **4. Filter Configuration**
```bash
# # From any device on the network: http://<raspberry-pi-ip>:3000
# Enable default filter lists (AdGuard DNS filter, OISD)
# Add custom domain blocklists as needed
# Configure safe search and parental controls (optional)
# Set up query logging preferences

```
### **5. Advance Configuration**
#### 1. IPv6 Configuration
```bash
# Ensure IPv6 is properly configured in AdGuard Home
# Settings → DNS Settings → Listen Addresses
# Add both IPv4 and IPv6 addresses

```
#### 2. DNS-over-HTTPS (DoH)
```bash
# Configure upstream DNS servers with DoH
# Example: https://cloudflare-dns.com/dns-query

```
## **🎯 Skills Demonstrated**
- Network Architecture Design: Implemented DNS-level filtering for entire network
- Linux System Administration: Raspberry Pi OS configuration and service management
- DNS Protocol Expertise: IPv4/IPv6, DoH, DoT, and DNS query handling
- Network Security: Implemented preventive measures against tracking and malware
- Power Efficiency Optimization: Selected and configured low-power hardware for 24/7 operation
- Troubleshooting: Resolved network manager conflicts (NetworkManager vs systemd)
- Documentation: Created comprehensive setup and configuration guides
- Monitoring & Analytics: Configured real-time DNS query monitoring

## 📁 Project Structure
home-dns-firewall/
├── README.md              # This file
├── docs/                  # Additional documentation
├── configs/              # Configuration templates
│   ├── adguardhome.yaml  # AdGuard Home configuration
│   └── network-setup.md  # Network setup guide
├── scripts/              # Automation scripts
│   ├── install.sh        # Installation script
│   └── update-filters.sh # Filter update script
└── images/               # Screenshots and diagrams

## 🚧 Challenges & Solutions

## 🔮 Future Enhancements


































