# AWS EC2 Security & Linux Admin Practice

## Overview

This project documents my process of securely setting up and managing an Amazon Linux EC2 instance on AWS. The steps below follow cloud best practices for user management, SSH hardening, updates, and basic monitoring.

---

## Steps Completed

1. **Launched a new EC2 instance (Amazon Linux 2023)**
2. **Connected via SSH using key pair**
3. **Created new admin user (`mehul`) and granted sudo access**
4. **Configured SSH key login for the new user**
5. **Disabled password authentication for SSH**
6. **Blocked login for the default `ec2-user` account**
7. **Updated the system for latest patches**
8. **(Optional) Installed and enabled firewalld**
9. **Monitored system security logs**

---

## Key Commands & Configuration

<pre> ```bash sudo adduser mehul 
  sudo passwd mehul 
  sudo usermod -aG wheel mehul ``` </pre>

### User Management

