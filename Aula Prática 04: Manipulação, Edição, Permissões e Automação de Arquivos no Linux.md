# Relatório Técnico: Introdução à Virtualização e Instalação do Ubuntu Server

## 1. Identificação
* **Nome completo:** Matheus Willian do Nascimento Oliveira
* **Curso:** Sistemas de Informação
* **Turma:** 2023.1
* **Data:** 12/08/2026
* **Título da prática:** Aula Prática 01: Introdução à Virtualização e Instalação do Ubuntu Server 26.04

---

## 2. Objetivo

Realizar prática de aprendizado, exercitando a manipulação de arquivos via bash, criando scripts, criando, editando, renomeando e movendo arquivos ao longo da estrutura do sistema operacional.  

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

A execução da atividade prática foi dividida nos seguintes passos sequenciais:

* **Criação da lista de usuários:** Utilizou-se o editor de texto Nano para criar o arquivo `usuarios.txt`, inserindo os 20 nomes de alunos (`aluno01` a `aluno20`) que seriam cadastrados.
* **Desenvolvimento do script de criação (`passo1_criar.sh`):** Foi escrito um script em Shell contendo um laço de repetição (`for`) para ler o arquivo `usuarios.txt` linha por linha e executar o comando de criação `useradd` (utilizando as flags `-m` para criar o diretório home e `-s /bin/bash` para definir o interpretador padrão).
* **Desenvolvimento do script de senhas (`passo2_senhas.sh`):** Criou-se um segundo script para definir as senhas de forma padronizada (senha igual ao próprio nome de usuário), enviando essas informações em lote para o utilitário `chpasswd`.
* **Permissões e Execução:** Aplicou-se a permissão de execução em ambos os scripts via modo simbólico (`chmod +x passo1_criar.sh passo2_senhas.sh`), executando-os sequencialmente no terminal.
* **Validação:** O sucesso da automação foi verificado consultando as bases do sistema via `getent passwd` e `getent group`, filtrando apenas os últimos 20 registros inseridos com o comando `tail -n 20`.

---

## 5. Testes e Validação


### Consultando base do sistema de senhas  
![getent passwd](./imagens/aula4/getnet%20passwd.png)


### Consultando base do sistema de usuários e grupos  
![getent group](./imagens/aula4/getent%20group.png)

### Login bem sucedido com o usuário 1  
![login_bem_sucedido](./imagens/aula4/login%20bem%20sucedido%20com%20aluno1.png)
---

## 6. Problemas e Soluções

Sem problemas encontrados durante as etapas do exercício.  

---

## 7. Conclusão

A manipulação de arquivos é um mecanismo essencial no gerenciamento do sistema operacional, o que permite ao usuário realizar livre manejo de como criar, organizar, e restringir o acesso aos arquivos, assim como criação e execução de scripts para otimização de ações no sistema.