# Ansible-ssh
Playbooks for ssh access and revoke operations

web servers info --------- webservers  (Inventory file)
ssh users info   --------- group_vars/users


Steps followed for testing the playbooks:

1) Created three servers on digitalocean. The servers ip addresses are mentioned inside the webservers file.
2) All the ssh_users related inforamtion can be modified inside group_vars/users file.
3) ssh access can given to all users on servers by running the following ansible playbook

    SSH-ACCESS:
       ansible-playbook -i webservers ssh-access.yml
       
       This playbook will copy the authorized-keys of each users and copy them onto the remote servers inside
       /etc/ssh/authorized_keys so that users can access to them. Make sure that sshd is restarted once modified.
     
    SSH-REVOKE:
       ansible-playbook -i webservers ssh-revoke.yml
  
       This playbook will delete the authorized keys from servers so that ssh is revoked for all users.
