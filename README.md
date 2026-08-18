# Home-Server Setup
This repository describes the setup process of my home server cluster consisting of one Zorin OS (linux based) machine with a GUI per remote desktop connection and one Ubuntu-Server machine for compute intensive tasks.

# 1) Zorin Machine - Remote Desktop

This 12-core machine was set up as a Linux server based on Zorin OS designed for visual remote access with a smooth, Windows-like desktop experience.

---

## System Overview
- CPU: 12 Cores
- No dedicated GPU
- OS: Zorin OS (Linux)
- Goal: Secure and fast remote desktop management over SSH and NoMachine with access ability from external networks.

---

## Setup Steps
After installing Zorin OS on the machine, the first step is to enable a SSH connection.

### 1. SSH & Security Foundation
- Installation & Activation: Verified and enabled the SSH service on the server for automatic startup.
- Firewall Protection: Configured the local firewall (UFW) to allow incoming SSH connections (Port 22).
- Key-Based Authentication: Generated an Ed25519 key pair on the client laptop and copied the public key to the server.
- File Permissions: Restricted access rights on the SSH configuration folder to the server user only.
- Disabled password authentication and root login, requiring public key authentication.

### 2. Network & Router Configuration (Fritz!Box)
- Static IP Address: Assigned a fixed internal IP address to the server on the local network.
- Local Inter-Device Communication: Enabled communication between active Wi-Fi devices in the router settings.
- Port Forwarding: Mapped a custom external port on the router to the server's internal SSH port.
- Dynamic DNS: Configured MyFritz! to ensure continuous access despite dynamic public IP changes.

### 3. Remote Desktop Setup (NoMachine)
- Solution Migration: Switched from initial RDP/xrdp testing to NoMachine due to 1-2 seconds lag with RDP.
- Installation: installed the NoMachine package on the server.
- SSH Port Tunneling: Kept native remote desktop ports closed to the public internet, routing traffic through an encrypted SSH tunnel (port forwarding).
- Client Connection: Established remote desktop sessions via the local forwarded tunnel port.

### 4. Hardening & Wake-on-LAN (WoL)
- Brute-Force Protection: Installed Fail2Ban to automatically detect and temporarily ban IPs after repeated failed login attempts.
- BIOS Adjustments: Disabled deep sleep states (S5) and power management restrictions while enabling Wake-on-LAN.
- Remote Booting: Configured the router to automatically wake the server from standby upon incoming external requests.

Now I am able to connect via SSH on my laptop from any network and have the server's screen mirrored in NoMachine.

# 2) Ubuntu Server Machine - Compute Backend

**This machine is currently still in the setup process. Once the configuration is complete, this page will be updated.**
