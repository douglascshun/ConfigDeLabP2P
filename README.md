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
<p align="center"><em>Laboratório de segurança isolado, automatizado e monitorado em tempo real</em></p>
<p align="center"><strong>Link Ponto a Ponto (P2P) · Montagem Persistente (SSHFS) · Monitoramento com Wazuh</strong></p>

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

<a href="#visao-geral"><img src="https://img.shields.io/badge/▸_VISÃO_GERAL-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/▸_BENEFÍCIOS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/▸_ARQUITETURA-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/▸_IMPLEMENTAÇÃO-000000?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> ⚠️ **Repositório em construção** — o guia completo está sendo documentado e publicado por etapas.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Visão Geral

Este repositório apresenta uma solução completa para montar um **Cyber Range / Laboratório de Segurança** totalmente isolado, rápido, automatizado e monitorado em tempo real.

O grande diferencial é **eliminar de vez** práticas manuais e inseguras como:
- Uso constante de `scp`, `sftp` e digitação de senhas
- Exposição de serviços críticos na rede Wi-Fi principal
- Falta de visibilidade do próprio servidor de segurança

Tudo isso é substituído por:
- Rede **P2P dedicada** (cabo direto ou virtual)
- Montagem persistente via **SSHFS** + autenticação por chave
- Monitoramento completo com **Wazuh** (incluindo o próprio Manager)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Benefícios e Problemas Resolvidos

| Problema Antigo | Solução Implementada | Benefício Final |
|-----------------|----------------------|-----------------|
| Exposição de serviços na rede Wi-Fi principal | Link P2P isolado + UFW restritivo | Isolamento total + velocidade máxima + superfície de ataque mínima |
| Uso constante de `scp`, `sftp` e senhas | SSHFS persistente + chave SSH | Arquivos remotos acessados como se fossem locais |
| Sem visibilidade do próprio Manager | Wazuh Agent 000 (localhost) + Agent P2P | Monitoramento 100% do ambiente, inclusive do servidor |

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Arquitetura

| Máquina | Função | IP (exemplo) | SO |
|---------|--------|--------------|----|
| Servidor (Manager) | Wazuh Manager + Dashboard + ambiente de trabalho | `10.10.10.1` | Kali / Debian |
| Notebook (Agent) | Máquina do analista / pentester | `10.10.10.2` | Kali / Debian |

### Pré-requisitos (já instalados)
- Wazuh Manager + Dashboard no servidor
- Wazuh Agent no notebook
- `sshfs` nas duas máquinas
- `ufw` ativo no servidor
- Deskflow / Barrier / Input Leap (para mouse/teclado compartilhado)

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Guia de Implementação

### Passo 1 — Link Ponto a Ponto (P2P)

**No Servidor (`10.10.10.1`)**
```bash
sudo nano /etc/network/interfaces
```

Adicione estas linhas ao arquivo:
```
auto eth0
iface eth0 inet static
    address 10.10.10.1
    netmask 255.255.255.0
```

> 🚧 **Próximos passos em breve:** configuração do Agent, SSHFS persistente, regras UFW e integração completa com o Wazuh.

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>
