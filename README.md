# Learning Ansible 

/configs/ansible/hosts - Inventory that holds all the hosts and groups

/configs/ansible/provisioning.yml - Playbook that has all the configurations that is used to configure remote machines

#### Basic command to execute in ansible VM

`ansible-playbook /vagrant/configs/ansible/provisioning.yml -u vagrant -i /vagrant/configs/ansible/hosts --private-key id_bionic`

#### Playbook

- hosts: indicates which hosts the configuration will be executed

- tasks: list of task that will be executed in target machine
  - name: name of the task that will be shown in console during execution
  - apt: package manager used by ansible to be used in target machine
    - name: name of the package to be installed
    - state: which state the installation should be after execution
  - become: indicates if should be executed as sudo (yes/no)
