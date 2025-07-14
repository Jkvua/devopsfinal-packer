### Aluna: Camila Ferreira de Almeida
---
# 📦 DevOpsFinal – Packer

Este repositório contém o projeto final da disciplina de DevOps, utilizando o **Packer** para automação de criação de imagens com provisionamento via **Ansible**, utilizando **Vagrant** e **VirtualBox** como base.

---

## 🛠️  Ferramentas Utilizadas

- 🧰 **Packer** – criação de imagens imutáveis
- 📦 **Vagrant** – gerenciamento de máquinas virtuais
- 📦 **VirtualBox** – provedor de virtualização
- 🤖 **Ansible** – provisionamento da imagem
- 🧪 **GitHub Actions** – integração contínua (CI) para validar templates e builds

---

## ✅ Pré-requisitos

Antes de executar o projeto, instale as seguintes ferramentas na sua máquina:

- [Packer](https://www.packer.io/downloads)
- [Vagrant](https://developer.hashicorp.com/vagrant/downloads)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html)

> **Dica:** Para sistemas baseados em Debian/Ubuntu, você pode instalar com:
> ```bash
> sudo apt install virtualbox vagrant ansible
> ```
---
## 🚀 Clone o Repositório
```
> git clone https://github.com/Jkvua/todolist-fullstack-backend.git
> cd todolist-fullstack-backend
```
---
## 🧰 Siga os comandos na ordem
```
# comandos para iniciar o projeto packe e instalar os plugins necessários 
> packer init .
> packer plugin install github.com/hashicorp/virtualbox
> packer plugin install github.com/hashicorp/vagrant
# comando para criar a imagem
> packer build debian.json
# adicionar imagem ao grupo vagrant
> vagrant box add debian12 debian12.box
# executar o ambiente criado
> vagrant up
```
---
## 🔑 Gerar chave de SSH para autenticação sem senha
```
# de enter 🔘 em todos as opções
> ssh-keygen
# o comando acima gera um caminho - use no comando de baixo 
> ssh-copy-id -i <caminho da chave gerada> vagrant@<ip da maquina virtual gerada>
```
---
## 🆙 Executando o playbook do ansible
```
# na pasta ansible - execute
> ansible-playbook -i hosts install_nginx.yml
> ansible-playbook -i hosts install_configkub.yml

# fora da pasta ansible - execute
> ansible-playbook -i ansible/hosts argocd/task/apply.yml
```
---
## 👐 Abrinndo a aplicação
```
# no terminal - execute
> ssh@<ip_maquina_virtual>
# dentro da máquina virtual - execute -> abre no navegador <ip_maquina_virtual>:30444
> kubectl port-forward svc/provafinalfront-devops 30444:80 --address 0.0.0.0 -n default 
# dentro da máquina virtual - execute -> abre no navegador <ip_maquina_virtual>:30333
> kubectl port-forward svc/provafinalfront-devops 30333:80 --address 0.0.0.0 -n default 
```
--- 
## 📂 Pastas e arquivos importantes
Foram criadas duas importantes pastas para a execusão desse trabalho 📂ansible e 📂argocd
📂 Ansible -> possui os arquivos de instalção que executa a instalação das seguintes ferramentas
- Instalação do NGINX
- Docker e suas dependêcias
- Kind e Kubectl
- ArgoCD
- Criação de clusters nós
📂 ArgoCD -> possui arquivos para a aplicação dos repositórios no argocd
---
## 🔚 Finalizado
Assim concluímos o trabalho final de Fundamentos de DevOps com uma infraestrutura e deploy contínuo usando:
- 🤖 provisionamento
- ⚙️ criação de um cluster
- 🧰 packer
- 👩‍💻 técnicas de devops 
