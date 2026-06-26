---
layout: default
title: "Headless Raspberry Pi Home Server & Infrastructure Services"
description: "Deploying a low-power, high-availability headless server to manage localized media storage, network-wide DNS sinkholing, and remote streaming infrastructure."
category: project
---

### Project Overview
This project involves building and maintaining a 24/7 dedicated low-power home server designed to handle critical network services, local network storage, and media transcoding pipelines. Operating strictly in a headless configuration, the environment maximizes system performance and uptime, serving as the central backbone for private cloud functions and network infrastructure management.

---
### Core Deployments & Services

#### 1. Centralized Network Storage (Samba Media Server)
A dedicated, local network-attached storage solution configured for low-latency file sharing, data preservation, and local backups across all domestic client devices.
* **Implementation:** Standardized Samba (SMB) implementation managing a dedicated high-capacity external USB hard disk.
* **Performance:** Connected directly via Gigabit Ethernet (LAN) to bypass wireless interference, providing maximum throughput and minimal latency for raw file operations, concurrent client access, and seamless playback.

#### 2. Network-Wide Privacy & Security (Pi-hole DNS Sinkhole)
A network-wide utility that blocks advertisements, tracking scripts, and malicious telemetry before they reach client devices.
* **Implementation:** Self-hosted instance of Pi-hole compiled with customized blocklists and telemetry-blocking data sources.
* **Operational Mechanics:** Operates as a primary DNS sinkhole, intercepting DNS queries at the perimeter. Unwanted domains are dropped at the network layer, reducing bandwidth overhead, speeding up page load times, and enforcing baseline privacy across all devices on the network.

#### 3. Remote Streaming & Media Transcoding (Plex Media Server)
A media organization platform deployed to centralize local digital assets and facilitate remote access during transit.
* **Implementation:** Deployed via a Plex Media Server instance configured to leverage the underlying hardware footprint efficiently.
* **Performance Architecture:** Chosen over alternatives like Jellyfin due to its superior efficiency with limited processing resources. The deployment relies on standard hardware capabilities to transcode and stream clean, continuous standard-definition streams to external devices over cellular or remote networks without stalling the headless host.---
layout: default
title: "Self-Hosted Home Lab & Service Automation"
description: "Setting up an isolated local environment to run self-hosted services, Docker containers, and custom infrastructure configurations."
category: project
---

### Tech Stack
* **Hardware:** Raspberry Pi 4, Metallic Passive/Active Cooling Case, Dual CPU Fans, External USB Storage
* **OS:** Debian 12 (Bookworm) Custom Minimal / Headless Image
* **Networking & Protocols:** SSH, SMB/CIFS, DNS/DHCP, Plex Media Protocol

---

### Thermal Engineering & Infrastructure Reliability
Because the server hosts critical network architecture that cannot tolerate unexpected downtime, thermal mitigation was a core engineering focus:

* **Hardware Optimization:** Operating multiple sustained container services simultaneously increased thermal output. To prevent CPU thermal throttling and performance degradation, the stock chassis was upgraded to a heavy-duty metallic cooling case integrated with dual CPU fans.
* **High Availability Considerations:** This active cooling setup protects critical components, specifically the local DNS service. Preventing thermal failure removes network downtime risks, avoiding delays associated with fallback DNS routing switches.

---
