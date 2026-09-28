## 1. Identificação
* **Nome completo:** Matheus Willian do Nascimento Oliveira
* **Curso:** Sistemas de Informação
* **Turma:** 2023.1
* **Data:** 23/08/2026
* **Título da prática:** Aula Prática 06: Configuração de Rede Estática com Netplan e Modo Placa em Ponte (Bridge Adapter) no VirtualBox

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

## 4. Procedimento

O procedimento consistiu na reconfiguração do adaptador de rede no VirtualBox do modo NAT para o modo Bridge, seguida pela verificação prévia de um endereço IP livre na sub-rede do laboratório a partir do host Windows. Posteriormente, realizou-se a edição do arquivo de configuração do Netplan (/etc/netplan/00-installer-config.yaml) no Ubuntu Server para definir o IP estático, o gateway e os servidores DNS, aplicando e validando as ações solicitadas.

## 5. Testes e Validação

### 5.1 Ping para IP livre

![ping_ip_livre](./imagens/aula6/1.%20ping%20ip%20livre.png)

---

### 5.2 Virtual box em modo Bridge

![vbox_modo_bridge](./imagens/aula6/2.%20virtual%20box%20com%20modo%20bridge.png)

---

### 5.3 Arquivo de configuração de rede

![arquivo_de_configuracao_de_rede](./imagens/aula6/3.%20arquivo%20de%20configuracao%20de%20rede%20com%20ip%20livre.png)

---

### 5.4 Comando cat executado no arquivo de configuração

![comando_cat_executado_no_arquivo_de_configuração](./imagens/aula6/4.%20cat%20do%20arquivo%20de%20configuracao.png)

---

### 5.5 Comando ip addr no novo IP definido

![comando_ip_addr_no_novo_ip_definido](./imagens/aula6/5.%20ip%20addr%20com%20novo%20ip.png)

---

### 5.6 Comando ping do Windows para a VM

![comando_ping_do_Windows_para_a_vm](./imagens/aula6/6.%20ping%20windows%20para%20host.png)

---

### 5.7 Comando ping da VM para p Windows

![comando_ping_da_VM_para_p_windows](./imagens/aula6/7.%20ping%20vm%20para%20windows.png)

---

### 5.8 Comando traceroute nos endereços solicitados

![comando_traceroute_nos_endereços_solicitados](./imagens/aula6/8.%20traceroute%20para%20enderecos.png)

---

## 6. Problemas e Soluções

Não foram encontrados problemas durante a execução dos passos do script.

## 7. Conclusão

A prática evidenciou a importância técnica do uso de endereços IP estáticos e do modo Bridge em ambientes corporativos e de servidores, garantindo maior estabilidade, previsibilidade e comunicação direta com a rede física. Além disso, permitiu consolidar o uso do utilitário Netplan e de ferramentas de diagnóstico de conectividade para a administração de redes Linux.   

---