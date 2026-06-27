---
layout: default
title: "Raspberry Pi Home Server & Infrastructure Services"
description: "Deploying a low-power, high-availability headless server to manage localized media storage, network-wide DNS sinkholing, and remote streaming infrastructure."
category: project
---

## Raspberry Pi Home Server & Infrastructure Services

### Project Overview
I wanted to build a dedicated, low-power home server that could handle my media files and critical network services around the clock. To get the absolute best performance, it runs Debian 12 (Bookworm) in headless mode, and I manage everything completely through SSH. It’s my ultimate 24/7 workhorse which is power efficient and reliable.

---

### Core Deployments & Services

#### 1. File Server (Samba)
This is a simple NFS setup for storing and sharing all my files across the home. I also use it as a central spot to backup my files from different devices.
* **Implementation:** It runs a straightforward Samba setup with a high-capacity external USB hard disk for storage.
* **Performance:** I have it connected directly via LAN instead of Wi-Fi to get the best performance, giving me really low latency for fast file copying and smooth playback.


#### 2. Ad-Blocker (Pi-hole)
A must-have for every household. This handles ad blocking and privacy control across the entire network.
* **Implementation:** A self-hosted version of Pi-hole loaded up with custom blocklist sources.
* **Operational Mechanics:** It acts as a DNS sinkhole, blocking annoying ads and tracking scripts before they even reach my devices. The result is a clean, ad-free experience for every device in the house while protecting our privacy.


#### 3. Media Server (Plex)
This helps distribute locally stored media files to my Kodi home entertainment system and mobile devices. This is my absolute lifesaver when I am travelling. It lets me stream all my home media directly to my devices no matter where I am. There is built-in transcoding which adjusts the quality (like YouTube) to give optimized playback.
* **Implementation:** Deployed Plex server on Raspberry Pi to handle remote streaming. I use the free version, which works perfectly for streaming fair quality content when I'm away.
* **Performance Architecture:** I chose Plex because it is much better than Jellyfin when it comes to transcoding on limited hardware. Since the Pi only has basic hardware capabilities and no dedicated GPU, Plex keeps things running smoothly without choking the system.

---

### Tech Stack
* **Hardware:** Raspberry Pi 4, Metallic Cooling Case, Dual CPU Fans, External USB Storage
* **OS:** Debian 12 (Bookworm) Custom Minimal / Headless Image
* **Networking & Protocols:** SSH, SMB/CIFS, DNS/DHCP, Plex Media Protocol

---

### Thermal Engineering & Infrastructure Reliability
Because I run multiple services on this machine simultaneously, it generates a decent amount of heat. Keeping it cool was a major priority to ensure the network stays up:

* **Hardware Optimization:** To avoid thermal throttling under heavy loads, I upgraded the setup with a heavy-duty metallic cooling case and dual CPU fans. You can find the exact enclosure I used via this [Robocraze Metal Aluminium Case with Dual Fans](https://robocraze.com/products/raspberry-pi-metal-aluminium-case-with-double-fans-for-raspberry-pi-4b-black?variant=40193827471513) buy link.
* **High Availability Considerations:** Keeping the thermals down is critical because the Pi hosts crucial network architecture like my DNS server. If the Pi fails or overheats, I will face network issues and internet dropouts until the fallback DNS kicks in. This active cooling setup ensures things stay up and running smoothly.
---
