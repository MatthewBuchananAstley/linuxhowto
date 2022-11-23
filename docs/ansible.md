# Ansible 

IT automation tool

<a href="https://docs.ansible.com/ansible/latest/index.html">https://docs.ansible.com/ansible/latest/index.html</a>

# Installeer ansible

    pip3 install --user ansible

# Creëer inventory 

Daarvoor moet de directory /etc/ansible aangemaakt worden en ip adressen van (virtuele) machines toegevoegd worden aan een bestand "hosts". Bijvoorbeeld:

    [virtuelemachines]
    192.168.122.194

# Bekijk de machines in de inventory

    ansible all --list-hosts
    hosts (1):
    192.168.122.194


# Ansible ssh 

Ansible gebruikt ssh dus er moet een ansible ssh key pair aangemaakt worden en gekopieerd naar de virtuele machine:

    ssh-keygen -t rsa -f ansible_ssh_key 
    ...
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    ...

Twee keer een sterke passphrase invoeren <a href="https://github.com/MatthewBuchananAstley/vop/">Voice of pinocchio or pinocchia password generator</a>

Ansible useraccount aanmaken op de virtuele machine:

    useradd -m -U -d /home/ansible ansible

De key naar de virtuele machine kopieren:

    ssh-copy-id -i /home/username/.ssh/ansible_ssh_key.pub ansible@192.168.122.194
    /usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/username/.ssh/ansible_ssh_key.pub"
    /usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
    /usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
 

# Ping de hosts onder management via ansible user 

    ansible all -u ansible --private-key ~/.ssh/ansible_ssh_key -m ping 
    192.168.122.194 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    },
    "changed": false,
    "ping": "pong"
    }

# Inventory aanmaken 

Een inventory.yaml bestand aanmaken met daarin:

    virtuelemachines:
      hosts:
        centos01:
          ansible_host: 192.168.122.194

Het verifiëren van dat bestand kan met ansible-inventory:

    ansible-inventory -i inventory.yaml --list   
    {
        "_meta": {
            "hostvars": {
                "centos01": {
                    "ansible_host": "192.168.122.194"
                }
            }
    },
    "all": {
        "children": [
            "ungrouped",
            "virtuelemachines"
        ]
    },
    "virtuelemachines": {
        "hosts": [
            "centos01"
            ]
        }
    }

De management nodes pingen op groepnaam kan met behulp van het ansible commando:

    ansible -u ansible --private-key ~/.ssh/ansible_ssh_key virtuelemachines -m ping -i inventory.yaml 
    centos01 | SUCCESS => {
        "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python"
        },
        "changed": false,
        "ping": "pong"
    }
   
# Ansible variabelen

Met behulp van ansible variabelen kunnen commando regel argumenten gespecificieerd worden in het inventory bestand, bijvoorbeeld de usernaam en private key per host of hostgroep:  

    virtuelemachines:
      hosts:
        centos01:
          ansible_host: 192.168.122.194
          ansible_user: ansible
          ansible_private_key_file: /home/usernaam/.ssh/ansible_ssh_key


    ansible virtuelemachines -m ping -i inventory.yaml 
    centos01 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
        },
        "changed": false,
        "ping": "pong"
    }

<a href="https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html#variables-in-inventory">Ansible variabelen</a>

