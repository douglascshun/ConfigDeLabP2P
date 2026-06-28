<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Português-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-1987F0?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Español-555555?style=for-the-badge" alt="Español"/></a>
</div>

<!-- ══════════════════════════ BANNER ══════════════════════════ -->
<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
  <img src="https://www.pulsetechnology.com/hs-fs/hubfs/Cybersecurity%20Graphic.gif?width=1600&height=511&name=Cybersecurity%20Graphic.gif" width="100%" alt="Cybersecurity Banner"/>
</div>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<br/>

<h1 align="center">Cyber Range P2P</h1>
<p align="center"><em>Isolated, automated and real-time monitored security lab</em></p>
<p align="center"><strong>Point-to-Point Link (P2P) · Persistent Mount (SSHFS) · Monitoring with Wazuh</strong></p>

<div align="center">

<img src="https://img.shields.io/badge/Status-Em_construção-FFA500?style=for-the-badge" alt="wip"/>
<img src="https://img.shields.io/badge/Foco-Blue_Team_%7C_Lab-1987F0?style=for-the-badge" alt="foco"/>
<br/>
<img src="https://img.shields.io/badge/Wazuh-3A8DFF?style=flat-square&logo=wazuh&logoColor=white" alt="wazuh"/>
<img src="https://img.shields.io/badge/SSHFS-005571?style=flat-square&logo=openssh&logoColor=white" alt="sshfs"/>
<img src="https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white" alt="kali"/>
<img src="https://img.shields.io/badge/Debian-A81D33?style=flat-square&logo=debian&logoColor=white" alt="debian"/>
<img src="https://img.shields.io/badge/UFW-EE0000?style=flat-square" alt="ufw"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#visao-geral"><img src="https://img.shields.io/badge/▸_OVERVIEW-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/▸_BENEFITS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/▸_ARCHITECTURE-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/▸_IMPLEMENTATION-000000?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> ⚠️ **Repository under construction** — the complete guide is being documented and published in stages.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Overview

This repository presents a complete solution to set up a fully isolated, fast, automated and real-time monitored **Cyber Range / Security Lab**.

The key differentiator is to **permanently eliminate** manual and insecure practices such as:
- Constant use of `scp`, `sftp` and password typing
- Exposure of critical services on the main Wi-Fi network
- Lack of visibility into the security server itself

All of this is replaced by:
- Dedicated **P2P network** (direct or virtual cable)
- Persistent mount via **SSHFS** + key-based authentication
- Complete monitoring with **Wazuh** (including the Manager itself)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Benefits and Problems Solved

| Old Problem | Implemented Solution | Final Benefit |
|-----------------|----------------------|-----------------|
| Exposure of services on the main Wi-Fi network | Isolated P2P link + restrictive UFW | Total isolation + maximum speed + minimal attack surface |
| Constant use of `scp`, `sftp` and passwords | Persistent SSHFS + SSH key | Remote files accessed as if they were local |
| No visibility into the Manager itself | Wazuh Agent 000 (localhost) + P2P Agent | 100% monitoring of the environment, including the server |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Architecture

| Machine | Role | IP (example) | OS |
|---------|--------|--------------|----|
| Server (Manager) | Wazuh Manager + Dashboard + workstation environment | `10.10.10.1` | Kali / Debian |
| Laptop (Agent) | Analyst / pentester machine | `10.10.10.2` | Kali / Debian |

### Prerequisites (already installed)
- Wazuh Manager + Dashboard on the server
- Wazuh Agent on the laptop
- `sshfs` on both machines
- `ufw` active on the server
- Deskflow / Barrier / Input Leap (for shared mouse/keyboard)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Implementation Guide

### Step 1 — Point-to-Point Link (P2P)

**On the Server (`10.10.10.1`)**
```bash
sudo nano /etc/network/interfaces
```

Add these lines to the file:
```
auto eth0
iface eth0 inet static
    address 10.10.10.1
    netmask 255.255.255.0
```

> 🚧 **Next steps coming soon:** Agent configuration, persistent SSHFS, UFW rules and full integration with Wazuh.

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>
