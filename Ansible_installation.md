Update package lists and upgrade existing packages: The script uses apt package manager to update the list of available packages and upgrade any existing packages on the system.

Install required packages: The script installs the software-properties-common package, which provides tools for managing software repositories in Ubuntu/Debian-based systems.

Add Ansible repository and install Ansible: The script adds the official Ansible repository and installs Ansible using apt. Ansible is a popular open-source automation tool used for configuration management, provisioning, and orchestration of IT infrastructure.

Configure Ansible: The script sets up the default configuration for Ansible by creating an ansible.cfg file with specific settings. This includes setting the inventory file location to /etc/ansible/hosts, using the root user for sudo operations, and disabling host key checking for easier automation.

Create SSH key pair: The script generates a new SSH key pair using ssh-keygen command. SSH keys are used for authentication and secure communication between systems, and the generated key pair consists of a private key (id_rsa) and a public key (id_rsa.pub).

Restart SSH daemon: The script restarts the SSH daemon (sshd) to apply any changes made to SSH configuration, including the newly generated SSH key pair.

Print public key for manual copying: The script displays the content of the generated public key (id_rsa.pub) on the terminal, which can be manually copied and used for authentication on remote systems.






## Ansible Setup

This script sets up Ansible on an Ubuntu/Debian-based system.

```bash
#!/bin/bash

# Update package lists and upgrade existing packages
sudo apt update -y
sudo apt upgrade -y

# Install required packages
sudo apt install -y software-properties-common

# Add Ansible repository and install Ansible
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install -y ansible

# Configure Ansible
sudo sh -c 'echo -e "[defaults]\ninventory = /etc/ansible/hosts\nsudo_user = root\nhost_key_checking = False" > /etc/ansible/ansible.cfg'

# Create SSH key pair
sudo ssh-keygen

# Restart SSH daemon
sudo systemctl restart sshd

# Print public key for manual copying
echo "Your SSH public key:"
cat ~/.ssh/id_rsa.pub
```

### FOR WORKING NODE 

Update package lists and upgrade existing packages using apt.
Change to the home directory using cd.
Create a .ssh directory if it doesn't exist already, using mkdir -p.
Open the authorized_keys file in Vim for editing using vim. You may need to add public keys to this file to enable SSH access for authorized users.
Restart the SSH daemon using systemctl restart sshd to apply changes.
Print a message indicating that the working node setup is completed.

```#!/bin/bash

# Update package lists and upgrade existing packages
sudo apt update -y
sudo apt upgrade -y

# Change to home directory
cd ~

# Create .ssh directory if not exists
mkdir -p ~/.ssh

# Open authorized_keys file in vim for editing
sudo vim ~/.ssh/authorized_keys

# Restart SSH daemon
sudo systemctl restart sshd

echo "Working node setup completed!"
```

