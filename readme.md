# Ansible Example Lab


### Ansible Commands

Have ansible test connection to all hosts in the inventory file.  All can be subsituted for a inventory group. 
* ```ansible all -m ping```

Run an ansible playbook
* ```ansible-playbook --ask-vault-pass some_playabook.yml```

Encrypt a Variables Vault File
* ```ansible-vault encrypt vault.yml```

Decrypt a Variable file so it can be edited
* ```ansible-vault decrypt vault.yml```

### Ansible Directory Structure

```
├── hosts                       # Inventory of hosts.
├── ansible.cfg                 # Ansible config with defaults, including location of hosts file.
├── playbook_name.yml           # Ansible Playbook, There can be multiple playbook files. Playbooks will reference roles. 
│
├── group_vars/                 # Folder where global variables are stored. 
│   └── all/
│       ├── vars.yml            # Global Variables file.
│       └── vault.yml           # Global Variables file that contains secrets.
│
├── roles/                      # Roles that get referenced in the playbook file. 
│   └── role_name1/
│       └── tasks/
│           └── main.yml
│   └── role_name2/
│       └── tasks/
│           └── main.yml
│
├── templates/                  # Templates that will get uploaded in Playbooks.
    └── template_name1.j2
    └── template_name2.j2
```