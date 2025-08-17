# Week 5 Kubernetes Project

Overview
This project demonstrates container orchestration using Kubernetes.  
The application is made up of three main components:  
- **Frontend**: A React app served using Nginx  
- **Backend**: A Node.js/Express API  
- **Database**: MongoDB (with persistence using StatefulSet + PVC)  

These components are deployed to a Kubernetes cluster and connected using Services.  

---

🛠 Deployment
1. Clone the repository  
```bash
git clone https://github.com/EvelyneAkeyo/yolo.git
cd yolo
