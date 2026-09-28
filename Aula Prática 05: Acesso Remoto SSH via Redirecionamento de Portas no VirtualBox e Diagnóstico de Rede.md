## 1. Identificação
* **Nome completo:** Matheus Willian do Nascimento Oliveira
* **Curso:** Sistemas de Informação
* **Turma:** 2023.1
* **Data:** 12/08/2026
* **Título da prática:** Aula 05 - Acesso Remoto SSH via Redirecionamento de Portas no VirtualBox e Diagnóstico de Rede

---

## 2. Objetivo

O objetivo da atividade foi aprender a verificar as rotas da rede, acompanhar as portas e conexões usando o `netstat` e fazer uma conexão remota por SSH entre o Windows e o Ubuntu Server usando o NAT do VirtualBox.

---

## 3. Ambiente
* **Hardware Físico (Host):**
  * **Processador:** AMD Ryzen 5 5600GT
  * **Memória RAM:** 16 GB DDR4 (3200 MHz)
  * **Placa-mãe:** ASUS TUF Gaming A520M-Plus  
* **Virtualizador:** Oracle VM VirtualBox versão 7.1.18r173720
* **Imagem ISO Utilizada:** `ubuntu-22.04.5-live-server-amd64.iso`
* **Configurações da Máquina Virtual (Guest):**
  * **Nome da VM:** `ubuntu_server`
  * **Tipo / Versão:** Linux / Ubuntu (64-bit)
  * **Processador:** 1 vCPU
  * **Memória RAM:** 2048 MB 
  * **Armazenamento:** Disco rígido virtual de 32 GB 
  * **Controladora de Rede:** Interface em modo NAT (`enp0s3`) com DHCP ativo

---

## 4. Procedimento

Primeiro, foram instalados os programas `net-tools` e `traceroute` e foi verificado se o `openssh-server` estava instalado. Depois, foram usados os comandos `route -n`, `w`, `ipconfig` e `netstat -an` para verificar as informações da rede e das conexões. Por último, foi configurado o redirecionamento da porta no VirtualBox para permitir a conexão SSH com o Ubuntu Server.

---

## 5. Testes e Validação

### 5.1 Leitura do Estado da Rede com Netplan

![netplan_status](./imagens/aula5/1.netplan%20status.png)
---
### 5.2 Ifconfig

![ifconfig](./imagens/aula5/2.%20ifconfig.png)

---

### 5.3 Route -n

![route_n](./imagens/aula5/3.%20route%20-n.png)

---

### 5.4 Traceroute

![traceroute](./imagens/aula5/4.%20traceroute.png)

---

### 5.5 Comando Who

![who](./imagens/aula5/5.%20w.png)

---

### 5.6 Netsh -an sem linhas retornada

![net_sh_an](./imagens/aula5/6.%20netsh%20-%20an.png)

---

### 5.7 Netstat com redirecionamento

![netstat_com_redirecionamento](./imagens/aula5/7.%20netstat%20com%20redirecionamento.png)

---

### 5.8 Conexão via SSH

![conexao_via_ssh](./imagens/aula5/8.%20conexao%20via%20ssh.png)

---

### 5.9 Netsh após conexão ssh

![netsh_apos_conexao_ssh](./imagens/aula5/9.%20netsh%20apos%20conexao%20ssh.png)

---

### 5.10 Who com conexão

![who_com_conexao](./imagens/aula5/10.%20w%20com%20conexao.png)

---

## 6. Problemas e Soluções

Não foram encontrados problemas durante a execução dos passos do script.

---

## 7. Conclusão

Com a prática, foi possível entender melhor como funciona a comunicação entre o Windows e a máquina virtual. Os comandos utilizados ajudaram a verificar as conexões, as portas e as rotas da rede. Também foi possível perceber a importância de configurar corretamente o redirecionamento de portas para conseguir acessar o Ubuntu Server por SSH.
