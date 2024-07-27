# [en-us] Vagrant Apache Server Setup

## Overview

This repository provides a basic Vagrant setup for configuring an Apache web server and a database on a Debian virtual machine. This setup is intended for educational purposes and is not designed for production environments.

## Features

- **Apache Web Server**: Configures Apache on a Debian VM.
- **Database Setup**: Includes basic database setup (MariaDB or similar) for learning purposes.
- **Simple Configuration**: Aimed at simplicity and ease of use for development and study.

## Requirements

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)

## Plugins Used

- **[vagrant-faster](https://github.com/tmatilai/vagrant-faster)**: Speeds up Vagrant operations by caching box downloads and reusing them.
- **[vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest)**: Automatically installs the correct VirtualBox Guest Additions version for the VM.
- **VirtualBox**: The provider used for creating and managing the virtual machine.

## Setup

1. **Clone the Repository:**

   ```bash
   git clone git@github.com:jvlr95/vagrant-apache-server.git
   cd vagrant-apache-server
   ```

2. **Install Vagrant Plugins:**

   ```bash
   vagrant plugin install vagrant-faster
   vagrant plugin install vagrant-vbguest
   ```

3. **Configure VirtualBox Network:**

   You need to configure the VirtualBox network settings in `/etc/vbox/networks.conf`. For Vagrant, the following IP addresses were used:

   ```
   * 10.0.0.0/8 192.168.0.0/16
   * 2001::/64
   ```

4. **Start the Vagrant Environment:**

   ```bash
   vagrant up
   ```

   This command will start the VM, configure the Apache server, and set up the database.

5. **SSH into the VM:**

   Access the web server:

   ```bash
   vagrant ssh web
   ```

   or access the database VM:

   ```bash
   vagrant ssh data
   ```

6. **Access the Apache Server:**

   Open a web browser and navigate to `http://localhost:8090` to see the Apache server running.

## Note

Make sure to check the `Vagrantfile` for the `synced_folder` configuration. If you do not intend to use it, comment out the corresponding line in the `Vagrantfile`.

---

# [pt-br] Configuração do Servidor Apache com Vagrant

## Visão Geral

Este repositório fornece uma configuração básica do Vagrant para configurar um servidor Apache e um banco de dados em uma máquina virtual Debian. Esta configuração é destinada a fins educacionais e não é projetada para ambientes de produção.

## Recursos

- **Servidor Apache**: Configura o Apache em uma VM Debian.
- **Configuração de Banco de Dados**: Inclui uma configuração básica de banco de dados (MariaDB ou similar) para fins de aprendizado.
- **Configuração Simples**: Focada na simplicidade e facilidade de uso para desenvolvimento e estudo.

## Requisitos

- [Vagrant](https://www.vagrantup.com/)
- [VirtualBox](https://www.virtualbox.org/)

## Plugins Utilizados

- **[vagrant-faster](https://github.com/tmatilai/vagrant-faster)**: Acelera as operações do Vagrant armazenando em cache os downloads de boxes e reutilizando-os.
- **[vagrant-vbguest](https://github.com/dotless-de/vagrant-vbguest)**: Instala automaticamente a versão correta das Adições para Convidado do VirtualBox na VM.
- **VirtualBox**: O provedor utilizado para criar e gerenciar a máquina virtual.

## Configuração

1. **Clone o Repositório:**

   ```bash
   git clone git@github.com:jvlr95/vagrant-apache-server.git
   cd vagrant-apache-server
   ```

2. **Instale os Plugins do Vagrant:**

   ```bash
   vagrant plugin install vagrant-faster
   vagrant plugin install vagrant-vbguest
   ```

3. **Configure a Rede do VirtualBox:**

   É necessário configurar as definições de rede do VirtualBox em `/etc/vbox/networks.conf`. Para o Vagrant, os seguintes endereços IP foram usados:

   ```
   * 10.0.0.0/8 192.168.0.0/16
   * 2001::/64
   ```

4. **Inicie o Ambiente Vagrant:**

   ```bash
   vagrant up
   ```

   Este comando iniciará a VM, configurará o servidor Apache e configurará o banco de dados.

5. **Acesse a VM via SSH:**

   Acesse o servidor web:

   ```bash
   vagrant ssh web
   ```

   ou acesse a VM do banco de dados:

   ```bash
   vagrant ssh data
   ```

6. **Acesse o Servidor Apache:**

   Abra um navegador e navegue até `http://localhost:8090` para ver o servidor Apache em funcionamento.

## Nota

Certifique-se de verificar o `Vagrantfile` para a configuração de `synced_folder`. Se você não pretende usá-la, comente a linha correspondente no `Vagrantfile`.
