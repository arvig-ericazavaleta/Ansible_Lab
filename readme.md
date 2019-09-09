# Ansible Example Lab


### Ansible Commands

Have ansible test connection to all hosts in the inventory file.  All can be subsituted for a inventory group. 
```ansible all -m ping```

Run an ansible playbook
```ansible-playbook --ask-vault-pass some_playabook.yml```

Encrypt a Variables Vault File
```ansible-vault encrypt vault.yml```

Decrypt a Variable file so it can be edited
```ansible-vault decrypt vault.yml```

### Ansible Directory Structure

```
├── hosts
├── ansible.cfg
├── playbook_name.yml
│
├── group_vars/
│   └── all/
│       ├── vars.yml
│       └── vault.yml
│
├── roles/
│   └── role_name1/
│       └── tasks/
│           └── main.yml
│   └── role_name2/
│       └── tasks/
│           └── main.yml
│
├── templates/
    └── template_name1.j2
    └── template_name2.j2
```