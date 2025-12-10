# 🌥️ Node-Contact-App-with-RDSF
```
A simple **Cloud Contact App** built using **Node.js + Express**, containerized with **Docker**, deployed on **AWS EC2**, and connected to **AWS RDS MySQL** database.  
It allows users to submit a username through UI which gets stored in the cloud database.

This project is perfect for **Cloud Computing / DevOps internships** and demonstrates real-world deployment.

---

## 🚀 Features

✔ Node.js + Express backend  
✔ Simple UI (HTML + CSS + JS)  
✔ Stores data in AWS RDS MySQL  
✔ Fully Dockerized  
✔ Deployment on AWS EC2  
✔ Docker image published on Docker Hub  
✔ Auto database create (my_app_db)  
✔ Auto table create (contacts)  

---

## 🛠 Tech Stack

**Backend**
- Node.js
- Express.js

**Database**
- AWS RDS (MySQL 8.0)

**Cloud**
- AWS EC2 (Ubuntu)

**Container**
- Docker

**Frontend**
- HTML, CSS, JavaScript

---
```
```
## 📦 Folder Structure

contact-app/
├── server.js
├── package.json
├── Dockerfile
└── public/
├── index.html
├── style.css
└── script.js
```
```
+---------------------+
| User Browser |
+----------+----------+
|
HTTP (80)
|
+----------v----------+
| AWS EC2 Instance |
| (Docker Container) |
| Node.js App |
+----------+----------+
|
3306 Port
|
+----------v----------+
| AWS RDS MySQL |
+---------------------+
```
```
# 🧰 HOW TO RUN
```
```

You can run this project in **three different ways**:
```
```
---

# 🟦 1️⃣ Run Locally (Without Docker)

### Clone Repository

```bash
git clone [<your_repo_url>](https://github.com/DevopsbyLalit/Node-Contact-App-with-RDS.git)
cd contact-app
```
```
Install Dependencies
npm install
```
```
Set Environment Variables
export DB_HOST="your-rds-endpoint"
export DB_USER="admin"
export DB_PASSWORD="yourpassword"
```
```
Start App
node server.js
```
```
Open:

http://localhost:3000
```

```
🐳 2️⃣ Run with Docker (Local Machine)

Build Docker Image

docker build -t yourname/contact-app:1.0 .

``
Run Container
docker run -d -p 80:3000 \
-e DB_HOST="your-rds-endpoint" \
-e DB_USER="admin" \
-e DB_PASSWORD="yourpassword" \
yourname/contact-app:1.0

Open:

http://localhost
```

```
🗃 AWS RDS Setup
Create RDS Database

Go to AWS → RDS

Create Database

Engine: MySQL 8.0

Template: Free-tier

DB Instance: db.t3.micro

Username: admin

Password: ********

Public Access: No

VPC Security Group:

Inbound: MySQL(3306) FROM EC2 Security Group

Database Name: my_app_db

```


```
☁ 3️⃣ Deploy on AWS (Production)
Step 1 — Launch EC2 (Ubuntu)

Region: ap-south-1 (Mumbai)

Instance: t2.micro

Allow:

SSH: 22

HTTP: 80

Connect:

ssh -i key.pem ubuntu@<EC2-Public-IP>

Step 2 — Install Docker on EC2

sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ubuntu

Step 3 — Pull Image from Docker Hub

docker pull lalit25/contact-app:1.0

Step 4 — Run Container on EC2

docker run -d -p 80:3000 \
-e DB_HOST="database-1.xxxxxx.ap-south-1.rds.amazonaws.com" \
-e DB_USER="admin" \
-e DB_PASSWORD="yourpassword" \
lalit25/contact-app:1.0

Open in browser:

http://<EC2-Public-IP>
```
```
how to chack data base
```
```
1 > =docker run -it --rm mysql:8.0 \
mysql -h <RDS-ENDPOINT> -u admin -p

2 > = SHOW DATABASES;

3 > = USE my_app_db;

4 > = SHOW TABLES;

5 > = SELECT * FROM contacts;

Output:

+----+--------------+
| id | username     |
+----+--------------+
|  1 | lalit        |
|  2 | admin        |
|  3 | test         |
+----+--------------+



