## WP Install

Ansible setup for setting up a VPS for WP Install

### Requirements

* Ansible

### Includes

* Configure SSH
  * Configures Port
* Configure Base
  * Upgrade System
  * Install System Packages
  * Install Editors
  * Create System User with Sudo privileges
  * Configure Firewall for Web use
* zsh
  * Includes ohmyzsh
* Mysql
  * Configures Root Password
  * Creates DB
  * Creates DB User with explicit privileges
* PHP
  * Installs PHP 7.4
  * Installs PHP Extensions
  * Configures php.ini
    * Error Reporting
    * Error Log
    * Max upload size / Post size
    * Fix Path Info - Off
  * Installs wp-cli
  * Installs composer
* NodeJS
  * Default is 14.x
* Nginx
  * Disables Apache
  * Enables Nginx on boot
* LetsEncrypt
  * Create TLS Cert for domain/www.domain
  * Uses DNS Validation via Cloudflare
* Wordpress
  * Configure Nginx server config with Https
  * Download Wordpress Core via wp-cli
  * Configures Wordpress via wp-cli
  * Install Wordpress with user credentials via wp-cli

### Installation

1. Copy example files

```
cp .envrc.example .envrc
cp inventory.example inventory
```

1. Install Requirements

```
ansible-galaxy install -r requirements.yml
```

1. Modify envrc and inventory to have the values required

1. Run Ansible via:

_Specify create_user_password when prompted for password_

```
ansible-playbook -i inventory initial-server-setup.yml -K
```

Run certain tags

```
ansible-playbook -i inventory initial-server-setup.yml --tags "zsh"
```
