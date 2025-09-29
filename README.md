# project-1-securing-aws-ec2
This project demonstrates the full setup and security hardening process for an Amazon Linux 2023 EC2 instance on AWS. It covers everything from first launch to creating secure admin users, disabling insecure logins, updating, and monitoring a complete checklist for cloud server hygiene!

🚀 Steps Completed
Bootstrapped an EC2 Instance with Amazon Linux 2023

Connected via SSH with key pair

Created a new admin user for secure access

Copied SSH key for new user & verified login

Disabled password authentication for SSH

Denied SSH access to default ec2-user account

System update for patches

(Optional) Set up and verified firewall rules

Inspected security logs

🛠️ Commands & Configuration
All commands shown assume you are starting from login as the default user (ec2-user). Adapt for your chosen usernames.

Create a New User
bash
sudo adduser mehul
sudo passwd mehul
sudo usermod -aG wheel mehul # gives sudo access
Set Up SSH Key for New User
bash
sudo mkdir /home/mehul/.ssh
sudo cp /home/ec2-user/.ssh/authorized_keys /home/mehul/.ssh/
sudo chown -R mehul:mehul /home/mehul/.ssh
sudo chmod 700 /home/mehul/.ssh
sudo chmod 600 /home/mehul/.ssh/authorized_keys
Test login via:

bash
ssh -i "/path/to/your/key.pem" mehul@<EC2-IP>
Harden SSH Configuration
Edit /etc/ssh/sshd_config

bash
sudo nano /etc/ssh/sshd_config
Add or edit:

text
PasswordAuthentication no
ChallengeResponseAuthentication no
DenyUsers ec2-user
Restart SSH service:

bash
sudo systemctl restart sshd
Update Packages
bash
sudo dnf update -y
(Optional) Configure Firewall
bash
sudo dnf install firewalld -y
sudo systemctl enable firewalld
sudo systemctl start firewalld
sudo firewall-cmd --list-all
Monitor Security Logs
bash
sudo less /var/log/secure
🎯 Key Learnings
Why not to use default admin accounts

The superiority of SSH keys over passwords

Least privilege principle in user management

Importance of regular system updates & log monitoring

Basics of Linux user, group, and file permissions

How to document cloud work for professional visibility

📸 Screenshots & Outputs (Recommended)
Add terminal screenshots here to showcase key achievements, for example:

Successful login as new user

sudo whoami command result

SSH config file showing security edits

📚 Resources
Amazon Linux 2023 Documentation

AWS EC2 Documentation

Linux Security Essentials

AWS Security Best Practices
