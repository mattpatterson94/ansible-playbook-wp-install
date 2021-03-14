## WP Install

An Ansible Playbook for setting up a VPS configured to serve a secure WordPress installation

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
  * Create TLS Cert for domain/alt.domain
  * Uses DNS Validation via Cloudflare
* Wordpress
  * Configure Nginx server config with Https
  * Download Wordpress Core via wp-cli
  * Configures Wordpress via wp-cli
  * Install Wordpress with user credentials via wp-cli

### Installation

1. Install Requirements

```
ansible-galaxy install -r requirements.yml
```

2. Configure Host

Either modify the example host or create a new host. Either way use the example host as a reference for the next steps.

2a. Add host/IP to `config/inventory.yml`.

2b. Update `host_vars`. Create a `$host/main.yml` for non-sensitive vars, and `$host/vault` for sensitive vars.

2c. Encrypt `vault` file once all the sensitive vars have been added and record the vault password somewhere safe.

```bash
ansible-vault encrypt config/host_vars/$host/vault
```

1. Run Ansible via:

```bash
ansible-playbook -K -i config/inventory.yml -l $host --ask-vault-pass bootstrap.yml
```

Run certain tags

```bash
ansible-playbook -K -i config/inventory.yml -l $host --ask-vault-pass bootstrap.yml --tags "install-wordpress"
```
