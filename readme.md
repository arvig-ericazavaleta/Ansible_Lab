# Ansible Example Lab

Ansible is a framework for automating across IT operations.  Ansible's Engine runs Playbooks, the automation language to describe IT application infrastructure.  Ansible is an Agentless architecture, only requiring SSH and Python to manage Linux hosts.  Ansible Playbooks are written in YAML which makes them easily human readable.  Tasks are executed in order which makes execution predictable. 

### Install Ansible on Ubuntu
```
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
```

### Ansible Definitions

* Inventory: an INI file that contains information about the servers you are managing.
* Facts: global variables containing information about the system, like network interfaces or operating system.
* Playbook: a YAML file containing a series of procedures that should be automated.
* Task: a block that defines a single procedure to be executed, e.g.: install a package.
* Module: a module typically abstracts a system task, like dealing with packages or creating and changing files. Ansible has a multitude of built-in modules, but you can also create custom ones.
* Role: a set of related playbooks, templates and other files, organized in a pre-defined way to facilitate reuse and share.


### Download this Lab
Enter the folder you want to download this repo into and run. 
```
git clone https://github.com/ericazavaleta/Ansible_Lab.git
```

### Ansible Commands

Have ansible test connection to all hosts in the inventory file.  All can be subsituted for a inventory group. 
* ```ansible all -m ping```

Display Facts for a particular host. 
* ```ansible all -m setup```

Run an ansible playbook
* ```ansible-playbook --ask-vault-pass some_playabook.yml```

Encrypt a Variables Vault File
* ```ansible-vault encrypt vault.yml```

Decrypt a Variable file so it can be edited
* ```ansible-vault decrypt vault.yml```

Useful Switches
* ```--ask-vault-pass``` Have ansible ask for the password to decrypt a vault 
* ```--check``` Do a dry run  
* ```--syntax-check```  Checks playbook syntax
* ```--step``` Step thru each task
* ```-vvvv``` Verbose Output

### Guide to YAML syntax
https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html


### General Guide to basic Ansible Playbooks
https://www.digitalocean.com/community/tutorials/configuration-management-101-writing-ansible-playbooks


### Guide to Ansible Vault
https://www.digitalocean.com/community/tutorials/how-to-use-vault-to-protect-sensitive-ansible-data-on-ubuntu-16-04


### Ansible Directory Structure

```
├── hosts                       # An INI file that contains Inventory of hosts.
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