🚀 Ansible Infrastructure Automation Project
📌 Overview

This project demonstrates a production-ready Ansible automation setup using roles, inventories, and best practices.
It automates web deployment, user & SSH key management, and OS patching with conditional reboot handling across multiple Linux servers.

The project is designed to be:

✔️ Modular (role-based)

✔️ Idempotent

✔️ Safe (--check mode compatible)

✔️ Interview & resume ready

🧱 Architecture

Control Node

Ubuntu Linux

Ansible installed

SSH key-based access to managed nodes

Managed Nodes

Ubuntu Linux

Nginx web servers

User accounts with SSH access

Patch management enabled

📂 Project Structure
ansible-project/
├── inventory
├── site.yml
├── group_vars/
│   ├── all.yml
│   ├── dev.yml
│   └── qa.yml
├── roles/
│   ├── web/
│   │   ├── tasks/main.yml
│   │   ├── templates/index.html.j2
│   │   ├── handlers/main.yml
│   │   └── defaults/main.yml
│   ├── users/
│   │   ├── tasks/main.yml
│   │   └── files/
│   │       ├── devuser.pub
│   │       └── qauser.pub
│   └── patch/
│       └── tasks/main.yml
└── README.md

⚙️ Roles Description
🔹 Web Role

Installs Nginx

Deploys HTML template using Jinja2

Supports dynamic variables via group_vars

Uses handlers to reload Nginx when required

🔹 Users Role

Creates Linux users using loops

Assigns sudo privileges

Manages SSH authorized keys

Handles Ansible --check mode safely

🔹 Patch Role

Upgrades system packages

Checks reboot requirement

Reboots system only when needed

Uses safe conditional logic

📄 Inventory Example
[webservers]
node1 ansible_host=172.31.x.x ansible_user=ubuntu
node2 ansible_host=172.31.x.x ansible_user=ubuntu

📦 Variables Example
group_vars/all.yml
app_message: "Welcome from Ansible Web Project"

users:
  - name: devuser
    groups: sudo
    shell: /bin/bash

  - name: qauser
    groups: sudo
    shell: /bin/bash

▶️ How to Run
🔍 Dry Run (Check Mode)
ansible-playbook -i inventory site.yml --check


✔️ Verifies changes without modifying servers

🚀 Actual Deployment
ansible-playbook -i inventory site.yml


✔️ Applies configuration to all managed nodes

🧪 Verification
Check Users
ansible -i inventory all -m shell -a "id devuser"
ansible -i inventory all -m shell -a "id qauser"

Check SSH Access
ssh devuser@<node_ip>

Check Web App
curl http://<node_ip>

🧠 Key Ansible Concepts Demonstrated

Role-based architecture

Variable precedence (group_vars, defaults)

Jinja2 templating

Loops with dictionaries

SSH key management

Idempotency

Check mode limitations and handling

Conditional reboots

🧩 Common Issues Handled

✔️ Undefined variables
✔️ SSH key lookup paths
✔️ authorized_key limitations in check mode
✔️ Safe reboot logic

🏆 Why This Project Matters

This project reflects real enterprise automation, not tutorial-level Ansible.
It closely matches tasks performed in:

SRE roles

DevOps roles

Platform Engineering

Infrastructure Automation teams

🔮 Future Enhancements

🔐 Ansible Vault for secrets

🌍 Environment-specific deployments (dev / qa / prod)

📊 CI pipeline with ansible-lint

🔔 Slack / Email notifications

📦 Ansible Galaxy role packaging

👤 Author

Dev Bhoite
DevOps / SRE Engineer
Automation • Cloud • CI/CD • Infrastructure as Code
