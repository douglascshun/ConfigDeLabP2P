# #(Aruivo completo ainda não postado)#
## Workflow de Cyber Range Segura e Automatizada 


**Implementação de Link Ponto a Ponto (P2P), Montagem Persistente (SSHFS) e Monitoramento de Segurança com Wazuh**

## Visão Geral

Este repositório apresenta uma solução completa para montar um **Cyber Range / Laboratório de Segurança** totalmente isolado, rápido, automatizado e monitorado em tempo real.

O grande diferencial é **eliminar de vez** práticas manuais e inseguras como:
- Uso constante de `scp`, `sftp` e digitação de senhas
- Exposição de serviços críticos na rede Wi-Fi principal
- Falta de visibilidade do próprio servidor de segurança

Tudo isso é substituído por:
- Rede P2P dedicada (cabo direto ou virtual)
- Montagem persistente via **SSHFS** + autenticação por chave
- Monitoramento completo com **Wazuh** (incluindo o próprio Manager)

## Benefícios e Problemas Resolvidos

| Problema Antigo                                      | Solução Implementada                              | Benefício Final                                          |
|------------------------------------------------------|---------------------------------------------------|----------------------------------------------------------|
| Exposição de serviços na rede Wi-Fi principal       | Link P2P isolado + UFW restritivo                 | Isolamento total + velocidade máxima + ataque mínimo    |
| Uso constante de `scp`, `sftp` e senhas              | SSHFS persistente + chave SSH                     | Arquivos remotos acessados como se fossem locais         |
| Sem visibilidade do próprio Manager                  | Wazuh Agent 000 (localhost) + Agent P2P           | Monitoramento 100% do ambiente, inclusive do servidor    |

## Arquitetura

| Máquina             | Função                                              | IP (exemplo) | SO            |
|---------------------|-----------------------------------------------------|--------------|---------------|
| Servidor (Manager)  | Wazuh Manager + Dashboard + ambiente de trabalho   | 10.10.10.1   | Kali / Debian |
| Notebook (Agent)    | Máquina do analista / pentester                     | 10.10.10.2   | Kali / Debian |

### Pré-requisitos (já instalados)
- Wazuh Manager + Dashboard no servidor
- Wazuh Agent no notebook
- `sshfs` nas duas máquinas
- `ufw` ativo no servidor
- Deskflow / Barrier / Input Leap (para mouse/teclado compartilhado)

## Guia de Implementação Detalhado

### Passo 1 – Link Ponto a Ponto (P2P)

**No Servidor (10.10.10.1)**
```bash
sudo nano /etc/network/interfaces
```
## Adicione essas linhas no seu arquivo
```
auto eth0
iface eth0 inet static
    address 10.10.10.1
    netmask 255.255.255.0
```
