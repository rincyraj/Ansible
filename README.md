Login to EC2 server and run
      a.sudo apt update
      b.sudo apt install ansible
      c.ansible --version
Ansible prerequisite: Enable passwordless authentiocation from Ansible installed server to target servers
How to enable passwordless authentication?
      a. run ssh-keygen command in  main(Ansible installed) and target server. Copy id_rsa.pub content of main server and paste the content in authorised key file of target server
      check the connection is established or not--> run ssh <privateIP> of target from Main server
Inventory file: Is the file in which we will  list the private ip address of all target servers. It can  placed in the same folder where the ansible playbooks are stored. if there are 100 servers we can group the servers
like
[dbservers] 
173.23.76.85
[webservers]
173.45.56.45
Difference between Ansible adhoc commands and ansible playbooks?
Ansible adhoc commands--> if the requirement is to run  simple one or two commands, will use ansible adhoc commands
Ansible ad-hoc commands are powerful one-liners used to perform quick tasks or gather information on managed hosts without requiring a playbook.
    eg:ansible -i inventory all -m "shell" -a "touch new_test_file" [it will run for all servers listed in inventory file] or if the change need to run only in dbservers ansible -i inventory dbservers -m "shell" -a "touch devops"
    -i refers the path of the inventory file
    -m means <module>: Specifies the Ansible module to use for the task. Examples include ping, shell, copy, apt, yum, service, etc.check file is created in target server
    -a means to refer the tasks need to perform
    ansible -i inventory all -m 'ini' -a 'ping'
  115  ansible -i inventory all -m ping
  116  ansible -i inventory all -m "shell" -a "uptime"
  117  pwd
  118  vi src_file
  119  ansible -i inventory all -m 'copy' -a "src=/home/ubuntu/src_file dest=/home/ubuntu/file.txt"

Ansible Playbooks--> if we want to run multiple commands, go with Ansible playbooks. it is written in yaml file that define a series of tasks to be executed on remote hosts. Playbooks allow you to automate configuration management, application deployment, and orchestration of infrastructure using Ansible
      
