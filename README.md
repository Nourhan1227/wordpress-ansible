# WordPress Deployment using Ansible

This project automates the deployment of a **WordPress website** using **Ansible**. The setup includes **Apache (httpd)**, **MariaDB**, and **PHP** running on **Amazon EC2 instances**. The architecture is divided into a **master node (controller)** and **worker nodes** (for WordPress and the database).

## 📌 Project Structure

```
wordpress-ansible/
├── group_vars/
│   ├── all.yml
├── host_vars/
│   ├── wordpress.yml
│   └── db.yml
├── inventory/
│   └── hosts.ini
├── roles/
│   ├── apache/
│   ├── mariadb/
│   └── wordpress/
├── playbook.yml
└── README.md
```

## ⚙️ Technologies Used

- **Ansible**
- **Amazon EC2**
- **Apache (httpd)**
- **MariaDB**
- **PHP**
- **WordPress**
- **YAML**

## 🚀 How It Works

1. **Inventory file** specifies the IPs and groups of the target machines.
2. **group_vars** and **host_vars** contain configuration variables.
3. **Roles** are used to modularize tasks:
   - `apache/`: Installs and configures Apache web server.
   - `mariadb/`: Sets up MariaDB server and WordPress database.
   - `wordpress/`: Downloads and configures WordPress.
4. The main playbook (`playbook.yml`) runs the tasks on the correct hosts in the proper order.

## ✅ Requirements

- Ansible installed on the master machine
- SSH access to EC2 instances
- Python installed on target nodes
- Security groups opened for ports: **80 (HTTP)** and **3306 (MariaDB)**

## 🛠️ How to Run

1. Clone the repo:
   ```bash
   git clone https://github.com/Nourhan1227/wordpress-ansible.git
   cd wordpress-ansible
   ```

2. Update the `inventory/hosts.ini` file with your EC2 instances' IPs.

3. Edit variables in `group_vars/` and `host_vars/` as needed.

4. Run the playbook:
   ```bash
   ansible-playbook -i inventory/hosts.ini playbook.yml
   ```

5. Access the WordPress site via the public IP of the WordPress server.
