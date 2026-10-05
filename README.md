<!-- ══════════════════════ IDIOMAS / LANGUAGES ══════════════════════ -->
<div align="center">
<a href="README.md"><img src="https://img.shields.io/badge/Portugu%C3%AAs-1987F0?style=for-the-badge" alt="Português"/></a>
<a href="README.en.md"><img src="https://img.shields.io/badge/English-555555?style=for-the-badge" alt="English"/></a>
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
    <img src="https://readme-typing-svg.demolab.com?font=VT323&size=30&duration=2600&pause=500&color=1987F0&center=true&vCenter=true&width=620&height=70&lines=Cyber+Range+P2P;Laboratorio+de+seguranca+isolado;SSHFS+%2B+Wazuh+%2B+UFW;Documentado+por+etapas" alt="Typing SVG"/>
  </a>
</div>

<h1 align="center">Cyber Range P2P</h1>
<p align="center"><em>Laboratório de segurança isolado, rápido e monitorado em tempo real, sem senhas digitadas no caminho.</em></p>
<p align="center"><strong>Link ponto a ponto · montagem persistente com SSHFS · monitoramento com Wazuh</strong></p>

<div align="center">

<img src="https://img.shields.io/badge/Status-Em_constru%C3%A7%C3%A3o-FFA500?style=for-the-badge" alt="wip"/>
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

<a href="#visao-geral"><img src="https://img.shields.io/badge/VIS%C3%83O_GERAL-1987F0?style=for-the-badge" alt="visao"/></a>
<a href="#beneficios"><img src="https://img.shields.io/badge/BENEF%C3%8DCIOS-000000?style=for-the-badge" alt="beneficios"/></a>
<a href="#arquitetura"><img src="https://img.shields.io/badge/ARQUITETURA-1987F0?style=for-the-badge" alt="arquitetura"/></a>
<a href="#roadmap"><img src="https://img.shields.io/badge/ROADMAP-000000?style=for-the-badge" alt="roadmap"/></a>
<a href="#implementacao"><img src="https://img.shields.io/badge/IMPLEMENTA%C3%87%C3%83O-1987F0?style=for-the-badge" alt="impl"/></a>

</div>

<br/>

> **Repositório em construção.** O guia completo está sendo documentado e publicado por etapas. O roadmap abaixo mostra com honestidade o que já está pronto e o que ainda vem.

<!-- ══════════════════════════ VISÃO GERAL ══════════════════════════ -->
<a id="visao-geral"></a>
## Visão geral

Este repositório documenta como montar um Cyber Range, um laboratório de segurança totalmente isolado, rápido, automatizado e monitorado em tempo real.

O ponto central é eliminar de vez três práticas manuais e arriscadas: o uso constante de `scp` e `sftp` com senha digitada, a exposição de serviços críticos na rede Wi-Fi principal e a falta de visibilidade sobre o próprio servidor de segurança. No lugar delas entram uma rede ponto a ponto dedicada, montagem persistente via SSHFS com autenticação por chave, e monitoramento completo com Wazuh cobrindo até o próprio Manager.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ BENEFÍCIOS ══════════════════════════ -->
<a id="beneficios"></a>
## Benefícios e problemas resolvidos

<div align="center">

| Problema antigo | Solução implementada | Benefício final |
|:--|:--|:--|
| Serviços expostos na rede Wi-Fi principal | Link P2P isolado com UFW restritivo | Isolamento total, velocidade máxima e superfície de ataque mínima |
| Uso constante de `scp`, `sftp` e senhas | SSHFS persistente com chave SSH | Arquivos remotos acessados como se fossem locais |
| Sem visibilidade do próprio Manager | Wazuh Agent 000 (localhost) e Agent P2P | Monitoramento de todo o ambiente, inclusive do servidor |

</div>

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ARQUITETURA ══════════════════════════ -->
<a id="arquitetura"></a>
## Arquitetura

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

| Máquina | Função | IP (exemplo) | SO |
|:--|:--|:--:|:--:|
| Servidor (Manager) | Wazuh Manager, Dashboard e ambiente de trabalho | `10.10.10.1` | Kali / Debian |
| Notebook (Agent) | Máquina do analista ou pentester | `10.10.10.2` | Kali / Debian |

</div>

**Pré-requisitos (já instalados nas duas máquinas):** Wazuh Manager e Dashboard no servidor, Wazuh Agent no notebook, `sshfs` nas duas pontas, `ufw` ativo no servidor e uma solução de mouse e teclado compartilhados (Deskflow, Barrier ou Input Leap).

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ ROADMAP ══════════════════════════ -->
<a id="roadmap"></a>
## Roadmap de implementação

O guia é dividido em cinco etapas. Conforme cada uma é validada na prática, ela é publicada aqui.

- [x] **Etapa 1 · Link ponto a ponto (P2P).** Configuração de IP estático nas duas máquinas. Publicada abaixo.
- [ ] **Etapa 2 · SSHFS persistente.** Montagem automática por chave, sobrevivendo a reboot.
- [ ] **Etapa 3 · Regras de UFW.** Liberação só do par P2P e bloqueio do resto.
- [ ] **Etapa 4 · Integração com o Wazuh.** Agent no notebook e Agent 000 no próprio Manager.
- [ ] **Etapa 5 · Mouse e teclado compartilhados.** Deskflow entre as duas máquinas.

<div align="center">
  <img src="https://64.media.tumblr.com/f444263be6597f8981d2b9cf3d0c7408/f74decdc69e61f0a-9a/s400x600/a157756e4c56be0e5e51a9e4c79ba781a451e94a.gifv" width="100%" height="2px" alt="divider"/>
</div>

<!-- ══════════════════════════ IMPLEMENTAÇÃO ══════════════════════════ -->
<a id="implementacao"></a>
## Guia de implementação

<details open>
<summary><b>Etapa 1 · Link ponto a ponto (P2P)</b></summary>

<br/>

**No servidor (`10.10.10.1`)**

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

A máquina do analista usa a mesma configuração, trocando o endereço para `10.10.10.2`.

</details>

<details>
<summary><b>Etapas 2 a 5</b> em breve</summary>

<br/>

Configuração do Agent, SSHFS persistente, regras de UFW, integração completa com o Wazuh e compartilhamento de mouse e teclado. O conteúdo entra aqui assim que cada etapa for validada.

</details>

<div align="center">
  <img src="https://file.loading.io/color/feature/thumb/Blues-8.png?" width="100%" height="10px" alt="divider"/>
</div>

<div align="center">
<a href="https://github.com/douglascshun"><img src="https://img.shields.io/badge/Perfil_GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="github"/></a>
<a href="https://www.linkedin.com/in/douglas-cshunderlick/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="linkedin"/></a>
<a href="mailto:douglascshun@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="email"/></a>
</div>

<br/>

<div align="center"><a href="#visao-geral"><img src="https://img.shields.io/badge/voltar_ao_topo-1987F0?style=flat-square" alt="topo"/></a></div>
