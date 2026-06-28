<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Português-555555?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-555555?style=for-the-badge" alt="English"/></a>
<a href="README.es.md"><img src="https://img.shields.io/badge/Español-1987F0?style=for-the-badge" alt="Español"/></a>
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
<p align="center"><em>Laboratorio de seguridad aislado, automatizado y monitorizado en tiempo real</em></p>
<p align="center"><strong>Enlace Punto a Punto (P2P) · Montaje Persistente (SSHFS) · Monitorización con Wazuh</strong></p>

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

<a href="#visao-geral"><img src="https://img.shields.io/badge/▸_VISIÓN_GENERAL-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/▸_BENEFICIOS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/▸_ARQUITECTURA-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/▸_IMPLEMENTACIÓN-000000?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> ⚠️ **Repositorio en construcción** — la guía completa está siendo documentada y publicada por etapas.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Visión General

Este repositorio presenta una solución completa para montar un **Cyber Range / Laboratorio de Seguridad** totalmente aislado, rápido, automatizado y monitorizado en tiempo real.

El gran diferencial es **eliminar de una vez** prácticas manuales e inseguras como:
- Uso constante de `scp`, `sftp` y escritura de contraseñas
- Exposición de servicios críticos en la red Wi-Fi principal
- Falta de visibilidad del propio servidor de seguridad

Todo esto se sustituye por:
- Red **P2P dedicada** (cable directo o virtual)
- Montaje persistente vía **SSHFS** + autenticación por clave
- Monitorización completa con **Wazuh** (incluyendo el propio Manager)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Beneficios y Problemas Resueltos

| Problema Antiguo | Solución Implementada | Beneficio Final |
|-----------------|----------------------|-----------------|
| Exposición de servicios en la red Wi-Fi principal | Enlace P2P aislado + UFW restrictivo | Aislamiento total + velocidad máxima + superficie de ataque mínima |
| Uso constante de `scp`, `sftp` y contraseñas | SSHFS persistente + clave SSH | Archivos remotos accedidos como si fueran locales |
| Sin visibilidad del propio Manager | Wazuh Agent 000 (localhost) + Agent P2P | Monitorización 100% del entorno, incluido el servidor |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Arquitectura

| Máquina | Función | IP (ejemplo) | SO |
|---------|--------|--------------|----|
| Servidor (Manager) | Wazuh Manager + Dashboard + entorno de trabajo | `10.10.10.1` | Kali / Debian |
| Portátil (Agent) | Máquina del analista / pentester | `10.10.10.2` | Kali / Debian |

### Requisitos previos (ya instalados)
- Wazuh Manager + Dashboard en el servidor
- Wazuh Agent en el portátil
- `sshfs` en ambas máquinas
- `ufw` activo en el servidor
- Deskflow / Barrier / Input Leap (para ratón/teclado compartido)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Guía de Implementación

### Paso 1 — Enlace Punto a Punto (P2P)

**En el Servidor (`10.10.10.1`)**
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

> 🚧 **Próximos pasos en breve:** configuración del Agent, SSHFS persistente, reglas UFW e integración completa con Wazuh.

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>
