Project 1: Open-Source Substation Automation System
Day 1 Documentation - December 6, 2024
Goals Accomplished Today

Created Ubuntu Server VM with OpenPLC runtime
Created Windows 10 VM for HMI/engineering workstation
Established host-only network between VMs
Verified OpenPLC web interface accessibility
System ready for ladder logic programming


Ubuntu Server VM Setup
VM Configuration

OS: Ubuntu Server 22.04 LTS
Server Name: REDACTED
Network Adapters:

Adapter 1: Host-only (192.168.X.X/24)
Adapter 2: NAT (for updates during setup, will be disabled for air-gap)



Network Configuration
Static IP Assignment:

IP Address: 192.168.X.X/24
Gateway: (none needed for host-only)
DNS: 8.8.8.8 (via NAT adapter)

Netplan Configuration (/etc/netplan/00-installer-config.yaml):
yamlnetwork:
  version: 2
  ethernets:
    enp0s3:  # Adapter 1 - Host-only
      addresses:
        - 192.168.X.X/24
      dhcp4: no
    
    enp0s8:  # Adapter 2 - NAT for internet
      dhcp4: yes
      nameservers:
        addresses:
          - 8.8.8.8
Applied with: sudo netplan apply
OpenPLC Installation
System Updates:
bashsudo apt update
sudo apt upgrade -y
Dependencies Installed:
bashsudo apt install -y git python3 python3-pip build-essential
OpenPLC Installation:
bashgit clone https://github.com/thiagoralves/OpenPLC_v3.git
cd OpenPLC_v3
./install.sh linux
Verification:
bashsudo systemctl status openplc
# Confirmed: active (running)

ss -tlnp | grep 8080
# Confirmed: Listening on 0.0.0.0:8080

Windows 10 VM Setup
VM Configuration

OS: Windows 10 Enterprise (Evaluation)
Network Adapter: Host-only (192.168.X.X/24)

Network Configuration
Static IP Assignment:

IP Address: 192.168.X.X
Subnet Mask: 255.255.255.0 (/24)
Default Gateway: (blank - not needed for lab network)
DNS: (blank - not needed for this VM)

Connectivity Testing
Ping Test:
cmdping 192.168.X.X
# Result: Successful - 4 replies received
```

**Web Interface Access:**
- URL: `http://192.168.X.X:8080`
- Result: OpenPLC login page loaded successfully
- Credentials verified: REDACTED

---

## Snapshots Created

**Ubuntu Server:**
- Snapshot Name: Snapshot 2
- State: OpenPLC installed, running, NAT adapter still enabled

**Windows 10:**
- Snapshot Name: Snapshot 1
- State: Networked and able to access OpenPLC web interface

---

## Lessons Learned

### Technical
- Netplan configuration requires exact YAML formatting (spacing matters)
- Initial configuration used /27 instead of /24 - corrected before applying
- `netstat` command not available by default; `ss` command works as alternative
- OpenPLC listens on 0.0.0.0:8080 (all interfaces) by default

### Process
- Breaking complex projects into daily goals maintains focus
- Natural stopping points prevent rushed learning
- Verification testing at each stage catches issues early
- Documentation during work is easier than reconstructing later

---

## Time Investment
- **Start Time:** 2:13 PM
- **End Time:** ~6:00 PM
- **Total Duration:** ~3.75 hours
- **Status:** Day 1 goals achieved

---

## System Architecture (Current State)
```
┌─────────────────────────────────────────┐
│         Host-Only Network               │
│         192.168.X.X/24                 │
│                                         │
│  ┌──────────────────┐  ┌─────────────┐ │
│  │  Ubuntu Server   │  │ Windows 10  │ │
│  │  (OpenPLC)       │  │ (HMI/Client)│ │
│  │  192.168.X.X    │  │ 192.168.X.X│ │
│  │                  │  │             │ │
│  │  Port 8080 open  │◄─┤  Browser    │ │
│  └──────────────────┘  └─────────────┘ │
│           │                             │
│  ┌────────▼────────┐                    │
│  │  NAT Adapter    │                    │
│  │  (To be disabled│                    │
│  │   for air-gap)  │                    │
│  └─────────────────┘                    │
└─────────────────────────────────────────┘

