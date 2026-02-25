
# Laboratório de Infraestrutura e Redes

Este repositório documenta a construção do meu ambiente de servidores, do zero até a segurança avançada.

## Estrutura do Projeto

### [Nível 1: Domínio e Active Directory](./nivel-1-gerenciamento-centralizado)
* Configuração do Servidor Windows 2022.
* Criação de usuários e grupos centralizados.

### [Nível 2: Integração Windows + Linux](./nivel-2-interoperabilidade)
* Conexão de uma estação Debian 13 ao servidor Windows.
* Compartilhamento de pastas na rede e permissões de acesso.
* Configuração de montagem automática no boot.

### [Nível 3: Gateway Linux, NAT e Roteamento de Rede](./nivel-3-gateway-roteamento)
* **Implementação de Gateway:** Configuração do Ubuntu Server como nó central entre WAN e LAN privada.
* **Domínio de NAT (Network Address Translation):** Uso de `iptables` e `IP Forwarding` para compartilhamento de internet.
* **Troubleshooting:** Diagnóstico e correção de conflito de endereçamento no Virt-Manager, erro de rota `onlink` no cliente Debian e ajuste de DNS Forwarders no Windows Server.
* **Persistência de Rede:** Aplicação de atributos de imutabilidade (`chattr`) para proteção de arquivos críticos de rede.

---
