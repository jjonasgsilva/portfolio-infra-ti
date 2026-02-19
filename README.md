<<<<<<< HEAD
# Projeto de Infraestrutura: Nível 1 - Gerenciamento Centralizado

## Descrição
Este laboratório foca na implementação de um Controlador de Domínio (DC) utilizando Windows Server 2022. O objetivo é estabelecer uma base centralizada para autenticação de usuários e gerenciamento de recursos de rede através do Active Directory.

## Topologia Lógica (Configuração de Rede)
* **IP Address:** 192.168.100.10
* **Subnet Mask:** 255.255.255.0
* **DNS Principal:** 127.0.0.1 (Loopback)

## Implementação Realizada
1. **Instalação de Binários:** Adição da função AD DS (Active Directory Domain Services) via Server Manager.
2. **Promoção de Domínio:** Criação de uma nova floresta chamada `lab.local`.
3. **Migração de Banco de Dados:** O servidor deixou de utilizar o banco SAM local e passou a utilizar o motor de banco de dados NTDS (Active Directory).

## Integração de Estação de Trabalho (Domain Join)
* **Host Cliente:** Windows 10 Pro
* **IP Address:** 192.168.100.20
* **DNS:** Apontando para o IP do DC (192.168.100.10)

## Processo de Ingresso
1. Configuração de conectividade IP e validação via comando `ping`.
2. Alteração do grupo de trabalho para o domínio `lab.local` utilizando credenciais administrativas.
3. **Pós-Ingresso:** Movimentação do objeto de computador do container padrão 'Computers' para a OU 'Computadores' visando futura aplicação de GPOs.
4. **Validação de Login:** Login efetuado com sucesso utilizando o usuário de domínio `joao.silva`.

## Verificações de Sucesso
- [x] Login realizado como `LAB\Administrador`.
- [x] Console 'Active Directory Users and Computers' operacional.
- [x] Estrutura de Unidades Organizacionais (OUs) e usuários iniciais criados.

### Validação de Conectividade e Rede
Para garantir o funcionamento do domínio, a pilha TCP/IP foi configurada manualmente:

* **Configuração de IP do Servidor:**
  ![IP Config Server](img/04-config-ip-server.png)

* **Teste de Comunicação e DNS (Cliente):**
  ![Ping e IP Cliente](img/05-validacao-rede-cliente.png)


## Gerenciamento de Políticas de Grupo (GPO)
Para demonstrar o controle centralizado, foi implementada uma política de segurança para exibição de aviso  antes do logon.

* **Nome da GPO:** `GPO-Aviso-Importante`
* **Escopo de Aplicação:** Aplicada (Linked) na OU `LAB-Principal`, afetando todos os computadores contidos nela.
* **Configurações Implementadas:**
    * *Interactive logon: Message text:* "Acesso restrito a pessoal autorizado!"
    * *Interactive logon: Message title:* "AVISO DA TI"
* **Comando de Atualização:** Utilizado o `gpupdate /force` na estação cliente para forçar a leitura imediata das novas diretrizes do servidor.

> **Nota Técnica:** O uso de GPOs vinculadas a OUs específicas (em vez de aplicá-las em todo o domínio) segue a boa prática de "Princípio do Menor Privilégio" e organização granular.


<details>
  <summary>Clique aqui para ver as evidências de configuração do AD e GPO</summary>

  <p>Estrutura de Unidades Organizacionais e Usuários:</p>

  <img src="img/01-estrutura-ad.png" alt="Print da tela de OUs" width="600">


  <p>Confirmação do login do usuário cliente no domínio</p>

  <img src="img/02-login-dominio.png" alt="Login do domnínio" width="600">
 

   <p>Organização após mover o objeto objeto de computador do container padrão 'Computers' para a OU 'Computadores'</p>

  <img src="img/03-organizacao-ou-computadores.png" alt="Objeto movido para OU Computadores" width="600">


  <p>Implementação da GPO de uma política de segurança para a exibição de um aviso antes do logon</p>

  <img src="img/06-implementacao-gpo.png" alt="Implementaçao de GPO com aviso antes do logon" width="600">


  <p>Banner de aviso configurado via GPO:</p>

  <img src="img/07-gpo-banner.png" alt="Print da tela de bloqueio com GPO" width="600">
</details>
=======
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
>>>>>>> 6a09ddd (Organizando estrutura de pastas e adcionando documentação do Nível 2)
