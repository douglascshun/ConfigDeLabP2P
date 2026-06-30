<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-1987F0?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Espa%C3%B1ol-555555?style=for-the-badge" alt="Español"/></a>
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

<div align="center">
  <a href="https://github.com/douglascshun/ConfigDeLabP2P">
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Cyber+Range+P2P;Isolated+security+laboratory;SSHFS+%2B+Wazuh+%2B+UFW;Documented+stage+by+stage" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cyber Range P2P</h1>
<p align="center"><em>An isolated, fast security lab monitored in real time, with no passwords typed along the way.</em></p>
<p align="center"><strong>Point-to-point link · persistent mount with SSHFS · monitoring with Wazuh</strong></p>

<div align="center">

<img src="https://img.shields.io/badge/Status-Under_construction-FFA500?style=for-the-badge" alt="wip"/>
<img src="https://img.shields.io/badge/Focus-Blue_Team_%7C_Lab-1987F0?style=for-the-badge" alt="foco"/>
<br/>
<img src="https://img.shields.io/badge/Wazuh-3A8DFF?style=flat-square&logo=wazuh&logoColor=white" alt="wazuh"/>
<img src="https://img.shields.io/badge/SSHFS-005571?style=flat-square&logo=openssh&logoColor=white" alt="sshfs"/>
<img src="https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white" alt="kali"/>
<img src="https://img.shields.io/badge/Debian-A81D33?style=flat-square&logo=debian&logoColor=white" alt="debian"/>
<img src="https://img.shields.io/badge/UFW-EE0000?style=flat-square" alt="ufw"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#visao-geral"><img src="https://img.shields.io/badge/OVERVIEW-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/BENEFITS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/ARCHITECTURE-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/ROADMAP-000000?style=for-the-badge" alt="roadmap"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/IMPLEMENTATION-1987F0?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> **Repository under construction.** The full guide is being documented and published stage by stage. The roadmap below is an honest view of what is already done and what is still to come.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Overview

This repository documents how to build a Cyber Range, a fully isolated, fast, automated security lab monitored in real time.

The core goal is to put an end to three manual, risky habits: the constant use of `scp` and `sftp` with a typed password, the exposure of critical services on the main Wi-Fi network, and the lack of visibility into the security server itself. In their place come a dedicated point-to-point network, a persistent SSHFS mount with key-based authentication, and full monitoring with Wazuh that reaches even the Manager itself.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Benefits and problems solved

<div align="center">

| Old problem | Implemented solution | Final benefit |
|:--|:--|:--|
| Services exposed on the main Wi-Fi network | Isolated P2P link with a restrictive UFW | Total isolation, maximum speed and minimal attack surface |
| Constant use of `scp`, `sftp` and passwords | Persistent SSHFS with an SSH key | Remote files accessed as if they were local |
| No visibility into the Manager itself | Wazuh Agent 000 (localhost) and P2P Agent | Monitoring of the whole environment, including the server |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Architecture

```mermaid
flowchart LR
    subgraph LAB[Cyber Range isolado]
      M["Servidor / Manager<br/>10.10.10.1<br/>Wazuh Manager + Dashboard"]
      A["Notebook / Agent<br/>10.10.10.2<br/>Estacao do analista"]
    end
    M <-->|"Link P2P dedicado<br/>SSHFS + UFW"| A
    style M fill:#1987F0,stroke:#000,color:#fff
    style A fill:#000000,stroke:#1987F0,color:#fff
```

<div align="center">

| Machine | Role | IP (example) | OS |
|:--|:--|:--:|:--:|
| Server (Manager) | Wazuh Manager, Dashboard and work environment | `10.10.10.1` | Kali / Debian |
| Laptop (Agent) | Analyst or pentester machine | `10.10.10.2` | Kali / Debian |

</div>

**Prerequisites (already installed on both machines):** Wazuh Manager and Dashboard on the server, Wazuh Agent on the laptop, `sshfs` on both ends, `ufw` active on the server and a shared mouse and keyboard solution (Deskflow, Barrier or Input Leap).

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Implementation roadmap

The guide is split into five stages. As each one is validated in practice, it is published here.

- [x] **Stage 1 · Point-to-point link (P2P).** Static IP setup on both machines. Published below.
- [ ] **Stage 2 · Persistent SSHFS.** Automatic key-based mount that survives a reboot.
- [ ] **Stage 3 · UFW rules.** Allow only the P2P peer and block the rest.
- [ ] **Stage 4 · Wazuh integration.** Agent on the laptop and Agent 000 on the Manager itself.
- [ ] **Stage 5 · Shared mouse and keyboard.** Deskflow between the two machines.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Implementation guide

<details open>
<summary><b>Stage 1 · Point-to-point link (P2P)</b></summary>

<br/>

**On the server (`10.10.10.1`)**

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

The analyst machine uses the same configuration, changing the address to `10.10.10.2`.

</details>

<details>
<summary><b>Stages 2 to 5</b> coming soon</summary>

<br/>

Agent setup, persistent SSHFS, UFW rules, full Wazuh integration and shared mouse and keyboard. The content lands here as soon as each stage is validated.

</details>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/GitHub_Profile-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>

<br/>

<div align="center"><a href="#visao-geral"><img src="https://img.shields.io/badge/back_to_top-1987F0?style=flat-square" alt="topo"/></a></div>
