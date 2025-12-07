# Power Substation Automation Lab

Open-source substation automation system for ICS/OT security research and training in the power sector.

## Project Overview

This project builds a functional substation simulation using entirely free and open-source tools, focusing on:
- ICS protocol implementation (Modbus TCP, progressing to DNP3)
- SCADA system configuration and operation
- Power sector network architecture (Purdue Model)
- Security monitoring and threat detection

## Current Status

🚧 **In Development** - Day 1 Complete

### Completed
- [x] Ubuntu Server VM with OpenPLC runtime
- [x] Windows 10 HMI workstation
- [x] Host-only network configuration (192.168.X.X/24)
- [x] OpenPLC web interface verified

### In Progress
- [ ] Ladder logic programming
- [ ] ScadaBR SCADA master integration
- [ ] Modbus TCP communication testing

## Architecture
```
┌─────────────────────────────────────────┐
│         Host-Only Network               │
│         192.168.X.X/24                 │
│                                         │
│  ┌──────────────────┐  ┌─────────────┐ │
│  │  Ubuntu Server   │  │ Windows 10  │ │
│  │  (OpenPLC)       │  │ (HMI/Client)│ │
│  │  192.168.X.X   │  │ 192.168.X.X│ │
│  └──────────────────┘  └─────────────┘ │
└─────────────────────────────────────────┘
```

## Technology Stack

- **PLC Runtime:** OpenPLC
- **SCADA Master:** ScadaBR (planned)
- **Protocol:** Modbus TCP → DNP3
- **Visualization:** Grafana + InfluxDB (planned)
- **Platform:** VirtualBox VMs (Ubuntu Server 22.04 LTS, Windows 10)

## Documentation

Daily progress documentation available in `/docs` directory.

## Skills Demonstrated

- ICS protocol implementation
- SCADA configuration
- Network architecture (Purdue Model)
- Power sector automation systems
- Technical documentation

## Learning Resources

Part of a structured power sector cybersecurity learning path. See `/docs/learning-guide.md` for curated resources.

## Project Timeline

- **Month 1-3:** Foundation projects (Substation automation, protocol analysis)
- **Month 4-6:** Malware analysis (CRASHOVERRIDE/Industroyer)
- **Month 7-12:** Advanced security (monitoring, red teaming, incident response)

## License

MIT License - See LICENSE file for details

## Contact

Building this project as part of career development in ICS/OT cybersecurity with focus on power sector security.

---

**Last Updated:** December 6, 2024

---
