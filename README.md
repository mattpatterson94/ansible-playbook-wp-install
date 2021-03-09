## WP Install

Ansible setup for setting up a VPS for WP Install

### Requirements

* Ansible

### Includes

*

### Installation

1. Copy example files

```
cp .envrc.example .envrc
cp inventory.example inventory
```

2. Modify envrc and inventory to have the values required

3. Run Ansible via:

```
ansible-playbook -i inventory initial-server-setup.yml
```

### Considerations

Generate Password:

```
python3 -c 'import crypt,getpass;pw=getpass.getpass();print(crypt.crypt(pw) if (pw==getpass.getpass("Confirm: ")) else exit())'
```
