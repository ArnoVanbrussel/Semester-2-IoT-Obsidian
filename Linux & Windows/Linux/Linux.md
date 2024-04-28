# Set Hostname

sudo nano /etc/hostname
> Change the Hostname: Replace the current hostname with "intranet" in the file. Delete the existing hostname and type "intranet". Save the changes and exit the text editor.

sudo nano /etc/hosts
> Edit the Hosts File: Find the line that starts with `127.0.0.1` and contains the existing hostname. Replace the existing hostname with "intranet". Additionally, if there's a line with the server's IP address and its current hostname, replace the hostname with "intranet" on that line as well. Save the changes and exit the text editor.

sudo hostnamectl set-hostname intranet
(sudo reboot)

# SSH Key Authentication

## Management
ssh-keygen -t rsa
ssh-copy-id user@intranet_ip
ssh user@intranet_ip
## Intranet
sudo nano /etc/ssh/sshd_config
	PubkeyAuthentication yes
	PasswordAuthentication no
sudo systemctl restart sshd
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

