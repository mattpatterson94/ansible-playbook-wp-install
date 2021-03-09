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

1. Install Requirements

```
ansible-galaxy install -r requirements.yml
```

1. Modify envrc and inventory to have the values required

1. Run Ansible via:

```
ansible-playbook -i inventory initial-server-setup.yml
```

Run certain tags

```
ansible-playbook -i inventory initial-server-setup.yml --tags "zsh"
```

Run with ssh/become password

```
ansible-playbook -i inventory initial-server-setup.yml  -kK
```

### Considerations

Generate Password:

```
python3 -c 'import crypt,getpass;pw=getpass.getpass();print(crypt.crypt(pw) if (pw==getpass.getpass("Confirm: ")) else exit())'
```
