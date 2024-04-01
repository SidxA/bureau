# general security
sudo apt update && sudo apt upgrade 

sudo apt install openssh-server

#CHOOSE PRIVATE PORT

#change default ssh port: modify /etc/ssh/sshd_config
#then connect with ssh -p 549 roman@192.168.1.10

#can do an autoconnect and alias using the ~/.bashrc file
alias <random-name>="ssh -p <SSH-PORT> <USERNAME>@<LOCAL-IP>"


#status
service ssh status
sudo systemctl status ssh

#maybe need to start?
sudo systemctl enable --now ssh

#allow through firewall
sudo apt install ufw
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 549/tcp comment 'SSH'
sudo ufw allow http
sudo ufw allow https
sudo ufw enable

#An additional layer of security can be gained by additionally blocking ping requests. For this, update the following line in /etc/ufw/before.rules
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP

sudo ufw reload


#key generation

#client machine
ssh-keygen -t rsa -b 4096 -C "<CLIENT-NAME>"

#Next, copy the public key to your server (mind the capital P to specify the non-standard SSH port)
scp -P 549 ~/.ssh/id_rsa.pub <YOURNAME>@<SERVER-IP>:/home/<YOURNAME>/.ssh/authorized_keys

#only accept ssh key-based authentication, edit the sshd_config file
PasswordAuthentication no
PermitRootLogin no

sudo service sshd restart

#FAIL2BAN
sudo apt install fail2ban

#copy the default fail2ban configuration file (make sure to end the custom file with .local)

sudo cp /etc/fail2ban/fail2ban.conf /etc/fail2ban/fail2ban.local

apend SSH jail to /etc/fail2ban/fail2ban.local

[sshd]
enabled = true
port = 549
filter = sshd
logpath = /var/log/auth.log
maxretry = 3
bantime = -1


sudo service fail2ban restart


#if accidently banned own device
sudo fail2ban-client set sshd unbanip 192.168.1.100

# python, cuda, pytorch