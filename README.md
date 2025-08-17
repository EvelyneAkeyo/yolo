🛒 YOLO E-Commerce platform (dockerized)

This project is a **full-stack shopping platform** built using React for the frontend, Node.js with Express for the backend API, and MongoDB for data storage. The entire stack is containerized using Docker and managed with Docker Compose.

---

🚀 Main capabilities

* View and add retail products
* Separate services for frontend, backend, and database
* Persistent MongoDB storage through named volumes
* Small and efficient builds using Alpine-based images
* Versioned and tagged Docker images (SemVer format: v1.0.0)
* Communication over a dedicated Docker bridge network

---

🧱 Tools and frameworks

| Layer    | Technology              |
| -------- | ----------------------- |
| Frontend | React + Nginx           |
| Backend  | Node.js + Express       |
| Database | MongoDB                 |
| Runtime  | Docker + Docker Compose |

---

🐳 DockerHub images

| Service  | Image                         |
| -------- | ----------------------------- |
| Frontend | `glen510/yolo-client:v1.0.0`  |
| Backend  | `glen510/yolo-backend:v1.0.0` |

---

🔧 Running the application

Clone the repository:

```bash
git clone https://github.com/your-username/yolo.git
cd yolo
```

Build and run all containers:

```bash
docker-compose up --build
```


📦 IP3 – Configuration management with ansible and vagrant

🔍 Overview

This independent project demonstrates how to **automate the deployment** of a containerized e-commerce application using **Vagrant** and **Ansible**.
It includes:

1. MongoDB — NoSQL data store
2. Backend API — Node.js + Express service
3. Frontend — React application served via Nginx

All components are deployed inside Docker containers on a **provisioned Ubuntu 20.04 VM**, with each setup step handled through modular Ansible roles.

---

🧰 Tech summary

| Tool    | Role in project                              |
| ------- | -------------------------------------------- |
| Vagrant | VM provisioning (Ubuntu 20.04 on VirtualBox) |
| Ansible | Automated setup and deployment               |
| Docker  | Container runtime                            |
| MongoDB | Persistent data store                        |
| Node.js | Backend API                                  |
| React   | Frontend UI                                  |

---

📂 Project layout

```
project-root/
├── Vagrantfile
├── playbook.yml
├── roles/
│   ├── mongodb/tasks/main.yml
│   ├── frontend/tasks/main.yml
│   └── backend/tasks/main.yml
├── terraform/        # (for later stages)
├── yolo/
│   ├── backend/
│   └── client/
├── explanation.md
└── README.md
```

---

🛠️ Vagrant setup

The **Vagrantfile provisions the VM, forwards necessary ports, and triggers the Ansible playbook.

```ruby
config.vm.box = "geerlingguy/ubuntu2004"

config.vm.network "forwarded_port", guest: 3000, host: 3000
config.vm.network "forwarded_port", guest: 5000, host: 5000
config.vm.network "forwarded_port", guest: 27017, host: 27017

config.vm.synced_folder ".", "/home/vagrant/yolo"

config.vm.provision "ansible" do |ansible|
  ansible.playbook = "playbook.yml"
end
```

---

📋 Ansible playbook structure
Step 1 – clone repository**
Ensures Git is installed and the latest app code is pulled.

Step 2 – Create docker network**
Sets up a custom bridge network so MongoDB, backend, and frontend can talk to each other:

```yaml
- name: Create Docker network app-net
  community.docker.docker_network:
    name: app-net
    state: present
```

Step 3 – Deploy containers via roles**
Roles are used for:

* MongoDB
* Backend API
* Frontend UI

---

🔄 Containers and images

| Container Name     | Image                          | Purpose       |
| ------------------ | ------------------------------ | ------------- |
| mongodb\_container | `mongo`                        | Data storage  |
| yolo-backend       | `glen510/yolo-backend:v1.0.0`  | API service   |
| yolofrontend       | `glen510/yolo-frontend:v1.0.0` | Web interface |

All are linked through the `app-net` Docker network.

---

💾 Data persistence

MongoDB uses a volume:

```yaml
volumes:
  - yolo_mongo_data:/data/db
```

This ensures data remains even if the MongoDB container is restarted or recreated.

---

🚀 How to deploy

1. Start VM:

   ```bash
   vagrant up
   ```
2. Connect:

   ```bash
   vagrant ssh
   ```
3. Run playbook:

   ```bash
   ansible-playbook playbook.yml
   ```

---

## 🌐 Access points

| Component | Address                                        |
| --------- | ---------------------------------------------- |
| Frontend  | [http://localhost:3000](http://localhost:3000) |
| Backend   | [http://localhost:5000](http://localhost:5000) |
| MongoDB   | localhost:27017                                |

---

## 🧠 Git Workflow example

```bash
git commit -m "Initial cleanup and setup"
git commit -m "Add Vagrantfile configuration"
git commit -m "Implement Ansible roles for MongoDB, backend, frontend"
git commit -m "Enable persistent storage for MongoDB"
git commit -m "Update README with deployment steps"
```

---

## 📌 Project overview

This project showcases the end-to-end automation of a full-stack web application deployment using Ansible and Vagrant. Key highlights include:

* Separation of deployment logic into roles
* Persistent data management for MongoDB
* Streamlined container orchestration
* Reproducible VM environment for development and testing

