# 📘 Automated Deployment of Note-Taking App using Ansible

## 🚀 Project Overview
This project demonstrates a complete **DevOps automation pipeline** to deploy a Python Flask web application on **AWS EC2** infrastructure using **Ansible**.

The project was developed as part of the **Digital Egypt Builders Initiative (DEBI)** scholarship program. It utilizes Ansible Roles to modularize the deployment process, ensuring scalability and reusability.

---

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
🤖 Automated Setup: Installs Python, Pip, Flask, and dependencies automatically without manual intervention.

⚙️ Service Management: Configures the app as a systemd service for reliability and auto-restart.

💾 Database Integration: Automatically initializes a SQLite database for storing notes locally.

🌐 Port Configuration: The application runs directly on Port 80 for HTTP access (No extra configuration needed).

🛡️ Backup Strategy: Includes a mechanism to secure data on a separate backend server.

⚙️ Prerequisites
Before running the playbook, ensure you have:

AWS Account: 3 running EC2 instances (Amazon Linux 2).

SSH Access: A .pem file with correct permissions:

chmod 400 key.pem

Security Group Rules:

Port 22 (SSH): Open from the Controller IP.

Port 80 (HTTP): Open to the world (0.0.0.0/0).

🚀 How to Run
Clone the Repository:

git clone [https://github.com/HassanMaher/note_app_role.git](https://github.com/HassanMaher/note_app_role.git)
cd note_app_role

2. Update Inventory
Edit the hosts file to add your EC2 Public IPs:

[web]
x.x.x.x ansible_user=ec2-user ansible_ssh_private_key_file=./key.pem

[db]
y.y.y.y ansible_user=ec2-user ansible_ssh_private_key_file=./key.pem

3. Run the Playbook
Execute the main playbook to start deployment:

ansible-playbook -i hosts deploy_notes.yml

4. Access the App
Once the playbook finishes successfully, open your browser and visit:

http://<WEB-SERVER-IP>

👨‍💻 Author
Hassan Maher

Role: Electronics & Communications Engineering Student

Program: DEBI Scholarship (DevOps Track)

GitHub : https://github.com/hassan-maher-dev

