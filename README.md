# 📘 Automated Deployment of Note-Taking App using Ansible

## 🚀 Project Overview
This project demonstrates a complete **DevOps automation pipeline** to deploy a Python Flask web application on **AWS EC2** infrastructure using **Ansible**.

The project was developed as part of the **Digital Egypt Builders Initiative (DEBI)** scholarship program. It utilizes Ansible Roles to modularize the deployment process, ensuring scalability and reusability.

## 🏗️ Architecture
The infrastructure consists of 3 AWS EC2 instances (Amazon Linux 2):

1.  **Ansible Controller:** Manages the configuration and deployment.
2.  **Web Server (Frontend):** Hosts the Python Flask application and the SQLite database.
3.  **Backup Server (Backend):** Acts as a secure storage for periodic database backups.

## 🛠️ Tech Stack
* **Infrastructure:** AWS EC2 (t2.micro).
* **Configuration Management:** Ansible (Roles & Playbooks).
* **Application:** Python 3 (Flask Framework).
* **Database:** SQLite (Embedded).
* **OS:** Amazon Linux 2.

---

## 📂 Project Structure
```text
.
├── hosts                   # Inventory file defining Web and Backup servers
├── deploy_notes.yml        # Main Playbook to orchestrate the deployment
├── roles/
│   └── note_app/           # The custom Ansible Role
│       ├── tasks/          # Main installation tasks
│       ├── handlers/       # Service restart handlers
│       ├── templates/      # Systemd service templates
│       ├── files/          # Source code (app.py)
│       └── meta/           # Galaxy metadata
└── README.md               # Project documentation

✨ Features
Automated Setup: Installs Python, Pip, Flask, and dependencies automatically.

Service Management: Configures the app as a systemd service for reliability.

Database Integration: Automatically initializes a SQLite database for storing notes.

Port Configuration: The application runs directly on Port 80 for HTTP access.

Backup Strategy: Includes a backup mechanism to secure data on a separate server.

⚙️ Prerequisites
Before running the playbook, ensure you have:

An AWS Account with 3 running EC2 instances.

SSH Key Pair (.pem file) with correct permissions (chmod 400 key.pem).

Security Group Rules:

Port 22 (SSH) open from the Controller.

Port 80 (HTTP) open to the world (0.0.0.0/0).

🚀 How to Run
Clone the Repository:

Bash
git clone [https://github.com/HassanMaher/note_app_role.git](https://github.com/HassanMaher/note_app_role.git)
cd note_app_role
Update Inventory:
Edit the hosts file with your EC2 Public IPs:

Ini, TOML
[web]
x.x.x.x ansible_user=ec2-user ansible_ssh_private_key_file=./key.pem

[db]
y.y.y.y ansible_user=ec2-user ansible_ssh_private_key_file=./key.pem
Run the Playbook:
Execute the deployment command:

Bash
ansible-playbook -i hosts deploy_notes.yml
Access the App:
Open your browser and visit: http://<WEB-SERVER-IP>

📸 Screenshots
(Place a screenshot of your running application here)

Example: A simple note-taking interface showing timestamped entries.

👨‍💻 Author
Hassan Maher

Role: Electronics & Communications Engineering Student

Program: DEBI Scholarship (DevOps Track)

