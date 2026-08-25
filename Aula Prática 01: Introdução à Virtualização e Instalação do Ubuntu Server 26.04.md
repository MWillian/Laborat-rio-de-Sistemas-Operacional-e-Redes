# Relatório Técnico: Introdução à Virtualização e Instalação do Ubuntu Server

## 1. Identificação
* **Nome completo:** Matheus Willian do Nascimento Oliveira
* **Curso:** Sistemas de Informação
* **Turma:** 2023.1
* **Data:** 12/08/2026
* **Título da prática:** Aula Prática 01: Introdução à Virtualização e Instalação do Ubuntu Server 26.04

---

## 2. Objetivo
Compreender os conceitos fundamentais de virtualização por meio da preparação do ambiente local no Oracle VM VirtualBox e da instalação limpa do sistema operacional Ubuntu Server. A prática teve como foco a configuração manual de armazenamento com particionamento LVM, definição de rede, criação de perfil administrativo e validação pós-instalação com atualização de pacotes.

---

## 3. Ambiente
* **Hardware Físico (Host):**
  * **Processador:** AMD Ryzen 5 5600GT
  * **Memória RAM:** 16 GB DDR4 (3200 MHz)
  * **Placa-mãe:** ASUS TUF Gaming A520M-Plus  
![preparação da VM sem a ISO carregada](./imagens/aula1/preparação%20da%20vm.png)

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
O processo foi dividido nas seguintes etapas principais:

1. **Criação da VM e Configuração de Mídia:**
   * A máquina virtual foi criada no diretório padrão com 1 vCPU e disco VDI de 32 GB dinâmico.
   * A imagem ISO `ubuntu-22.04.5-live-server-amd64` foi montada na controladora de armazenamento óptico.

2. **Inicialização e Idioma:**
   * O instalador do Ubuntu Server foi carregado em idioma *English*.
   * O teclado foi ajustado para o padrão *Portuguese (Brazil)*.
   * A placa de rede obteve endereço IP via DHCP na interface `enp0s3`. Configurações de Proxy e Mirror foram mantidas nos padrões.

3. **Particionamento Avançado com LVM (Custom Storage Layout):**
   * **Partição /boot:** Criada com tamanho de `1 GB` (1024 MB), formato `ext4` e ponto de montagem em `/boot`.
   * **Volume Group LVM:** Criado o grupo de volumes nomeado `ubuntu-vg` utilizando o restante do disco livre.
   * **Volume Lógico Raiz (/):** Criado o volume lógico `ubuntu-lv` com `29 GB`, formato `ext4` e ponto de montagem na raiz `/`.
   * **Volume Lógico Swap:** Criado o volume lógico `swap-lv` com `2 GB` (espaço restante) formatado como área de troca (*swap*).

4. **Configuração de Usuário e Serviços:**
   * No *Profile Setup*, foram definidas as credenciais padrão do laboratório:
     * *Your name:* `Administrador`
     * *Your server's name:* `ubuntu_server`
     * *Username:* `administrador`
     * *Password:* `adminifal`
---

## 5. Testes e Validação

### Listagem de endereços iP  

![Endereços IP](./imagens/aula1/endereço%20ip.png)  

### Atualização de pacotes  

![Atualização de pacotes](./imagens/aula1/sudo%20apt-get.png)

---

## 6. Problemas e Soluções
* **Problema Encontrado (Kernel Panic no Boot da ISO):**
  * *Descrição:* Ao iniciar o instalador do Ubuntu Server, o processo de boot foi interrompido abruptamente por um erro crítico de *Kernel Panic / Out of Memory*, impedindo a carga do instalador interativo.
  * *Causa:* A quantidade de memória RAM inicialmente atribuída à máquina virtual foi de 512 MB (conforme especificação do laboratório), valor insuficiente para descompactar o instalador em memória e carregar-lo.
  * *Solução:* A VM foi desligada e, nas configurações do VirtualBox (**Sistema > Placa-mãe > Memória Base**), a quantidade de memória RAM foi alterado de **512 MB** para **2048 MB (2 GB)**.

* **Problema Encontrado (Erro de Inicialização VERR_SVM_DISABLED):**
  * *Descrição:* Ao tentar ligar a máquina virtual pela primeira vez, o VirtualBox exibiu o erro `VERR_SVM_DISABLED` (Código `NS_ERROR_FAILURE`), impedindo a VM de iniciar.
  * *Causa:* A tecnologia de virtualização de hardware da AMD (AMD-V / SVM Mode) estava desativada por padrão na BIOS/UEFI da placa-mãe do Host.
  * *Solução:* O computador físico foi reiniciado e a BIOS acessada. No menu *Advanced Mode > CPU Configuration*, a opção *SVM Mode* foi alterada de *Disabled* para `Enabled`. Após salvar as alterações e reiniciar o sistema Windows, a VM ligou normalmente.

---

## 7. Conclusão
A prática permitiu consolidar na prática os conceitos de virtualização e o ciclo completo de instalação de um servidor Linux. A utilização do LVM evidenciou as vantagens do gerenciamento dinâmico e flexível de volumes em comparação com o particionamento tradicional. Adicionalmente, a resolução do problema de *Kernel Panic* deixou em evidência a importância de dimensionar corretamente a alocação de hardware virtual para atender aos requisitos mínimos dos sistemas operacionais modernos.