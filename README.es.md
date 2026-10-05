<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-555555?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Espa%C3%B1ol-1987F0?style=for-the-badge" alt="Español"/></a>
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
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Cyber+Range+P2P;Laboratorio+de+seguridad+aislado;SSHFS+%2B+Wazuh+%2B+UFW;Documentado+por+etapas" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cyber Range P2P</h1>
<p align="center"><em>Laboratorio de seguridad aislado, rápido y monitorizado en tiempo real, sin contraseñas escritas por el camino.</em></p>
<p align="center"><strong>Enlace punto a punto · montaje persistente con SSHFS · monitorización con Wazuh</strong></p>

<div align="center">

<img src="https://img.shields.io/badge/Status-En_construcci%C3%B3n-FFA500?style=for-the-badge" alt="wip"/>
<img src="https://img.shields.io/badge/Enfoque-Blue_Team_%7C_Lab-1987F0?style=for-the-badge" alt="foco"/>
<br/>
<img src="https://img.shields.io/badge/Wazuh-3A8DFF?style=flat-square&logo=wazuh&logoColor=white" alt="wazuh"/>
<img src="https://img.shields.io/badge/SSHFS-005571?style=flat-square&logo=openssh&logoColor=white" alt="sshfs"/>
<img src="https://img.shields.io/badge/Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white" alt="kali"/>
<img src="https://img.shields.io/badge/Debian-A81D33?style=flat-square&logo=debian&logoColor=white" alt="debian"/>
<img src="https://img.shields.io/badge/UFW-EE0000?style=flat-square" alt="ufw"/>

</div>

<!-- ══════════════════════════ NAVEGAÇÃO ══════════════════════════ -->
<div align="center">

<a href="#visao-geral"><img src="https://img.shields.io/badge/VISI%C3%93N_GENERAL-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/BENEFICIOS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/ARQUITECTURA-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/HOJA_DE_RUTA-000000?style=for-the-badge" alt="roadmap"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/IMPLEMENTACI%C3%93N-1987F0?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> **Repositorio en construcción.** La guía completa se está documentando y publicando por etapas. La hoja de ruta de abajo muestra con honestidad lo que ya está listo y lo que todavía falta.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Visión general

Este repositorio documenta cómo montar un Cyber Range, un laboratorio de seguridad totalmente aislado, rápido, automatizado y monitorizado en tiempo real.

El objetivo central es acabar de una vez con tres prácticas manuales y arriesgadas: el uso constante de `scp` y `sftp` con contraseña escrita, la exposición de servicios críticos en la red Wi-Fi principal y la falta de visibilidad sobre el propio servidor de seguridad. En su lugar entran una red punto a punto dedicada, un montaje persistente vía SSHFS con autenticación por clave, y una monitorización completa con Wazuh que alcanza hasta el propio Manager.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Beneficios y problemas resueltos

<div align="center">

| Problema antiguo | Solución implementada | Beneficio final |
|:--|:--|:--|
| Servicios expuestos en la red Wi-Fi principal | Enlace P2P aislado con un UFW restrictivo | Aislamiento total, velocidad máxima y superficie de ataque mínima |
| Uso constante de `scp`, `sftp` y contraseñas | SSHFS persistente con una clave SSH | Archivos remotos accedidos como si fueran locales |
| Sin visibilidad sobre el propio Manager | Wazuh Agent 000 (localhost) y Agent P2P | Monitorización de todo el entorno, incluido el servidor |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Arquitectura

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

| Máquina | Función | IP (ejemplo) | SO |
|:--|:--|:--:|:--:|
| Servidor (Manager) | Wazuh Manager, Dashboard y entorno de trabajo | `10.10.10.1` | Kali / Debian |
| Portátil (Agent) | Máquina del analista o pentester | `10.10.10.2` | Kali / Debian |

</div>

**Requisitos previos (ya instalados en ambas máquinas):** Wazuh Manager y Dashboard en el servidor, Wazuh Agent en el portátil, `sshfs` en ambos extremos, `ufw` activo en el servidor y una solución de ratón y teclado compartidos (Deskflow, Barrier o Input Leap).

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Hoja de ruta de implementación

La guía se divide en cinco etapas. A medida que cada una se valida en la práctica, se publica aquí.

- [x] **Etapa 1 · Enlace punto a punto (P2P).** Configuración de IP estática en ambas máquinas. Publicada abajo.
- [ ] **Etapa 2 · SSHFS persistente.** Montaje automático por clave que sobrevive a un reinicio.
- [ ] **Etapa 3 · Reglas de UFW.** Permitir solo el par P2P y bloquear el resto.
- [ ] **Etapa 4 · Integración con Wazuh.** Agent en el portátil y Agent 000 en el propio Manager.
- [ ] **Etapa 5 · Ratón y teclado compartidos.** Deskflow entre las dos máquinas.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Guía de implementación

<details open>
<summary><b>Etapa 1 · Enlace punto a punto (P2P)</b></summary>

<br/>

**En el servidor (`10.10.10.1`)**

```bash
sudo nano /etc/network/interfaces
```

Añade estas líneas al archivo:

```
auto eth0
iface eth0 inet static
    address 10.10.10.1
    netmask 255.255.255.0
```

La máquina del analista usa la misma configuración, cambiando la dirección a `10.10.10.2`.

</details>

<details>
<summary><b>Etapas 2 a 5</b> próximamente</summary>

<br/>

Configuración del Agent, SSHFS persistente, reglas de UFW, integración completa con Wazuh y uso compartido de ratón y teclado. El contenido aparece aquí en cuanto cada etapa se valida.

</details>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_de_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>

<br/>

<div align="center"><a href="#visao-geral"><img src="https://img.shields.io/badge/volver_arriba-1987F0?style=flat-square" alt="topo"/></a></div>
