# Deploying-Food-Delivery-App-On-AWS-Cloud

This project is a full stack food delivery application deployed on AWS with a strong focus on scalability, availability, and security, similar to how real production systems are designed. Instead of running everything on a single server, the application is divided into multiple layers so that each part can scale independently and remain secure.

The frontend of the application is deployed using an Auto Scaling Group that maintains a minimum of two EC2 instances. These instances are placed across different availability zones to ensure high availability. A public Application Load Balancer sits in front of these instances and distributes incoming user traffic evenly between them. To ensure a consistent public address for accessing the application, an Elastic IP is associated with the load balancer. Nginx is used on the frontend servers to host and serve the website efficiently.

Behind the frontend layer, the backend and admin services are deployed in private subnets, meaning they are completely isolated from direct internet access. These services are managed by a private Application Load Balancer, which receives requests only from the frontend layer and distributes them across multiple backend EC2 instances. This setup ensures that sensitive backend services are protected and can only be accessed internally within the VPC.

To allow backend and admin servers to access the internet for updates, package installations, or API calls, a NAT Gateway is deployed in a public subnet. The private EC2 instances route their outbound internet traffic through this NAT Gateway without exposing themselves publicly. This design maintains security while still allowing necessary external communication.

Overall, this architecture ensures that the application remains highly available, scalable under load, and secure by design. Traffic is carefully controlled at each layer, failures are handled gracefully through load balancing and auto scaling, and critical services are isolated within private networks. This project reflects real-world AWS cloud deployment practices rather than a basic single-server setup.

# 🍔 Full Stack Food Delivery App – AWS Cloud Deployment

This project demonstrates the deployment of a **scalable, production-style full stack food delivery application** on **Amazon Web Services (AWS)** using core cloud architecture principles such as **Auto Scaling, Load Balancing, Private Networking, and NAT Gateways**.

The main goal of this project is to showcase **real-world AWS infrastructure design**, not just application code.

---

## 🚀 Architecture Overview

The application is deployed using a **multi-tier architecture** consisting of:

- **Frontend Layer (Public)**
- **Backend & Admin Layer (Private)**
- **Networking & Security Components**
- **High Availability & Scalability**

---

## 🧱 Infrastructure Design

### 1️⃣ Frontend Layer
- **Auto Scaling Group (ASG)** with:
  - Minimum: 2 EC2 instances
  - Instances deployed across **multiple availability zones**
- **Application Load Balancer (Public)**
- **Elastic IP (EIP)** attached to the Load Balancer to provide a **consistent public endpoint**
- **Nginx** used to serve the frontend application

---

### 2️⃣ Backend & Admin Layer
- Deployed in **private subnets**
- Managed by a **Private Application Load Balancer**
- EC2 instances:
  - 2 × Backend servers
  - 2 × Admin backend servers
- Backend services are **not directly accessible from the internet**

---

### 3️⃣ Networking
- **VPC with Public and Private Subnets**
- **NAT Gateway** placed in a public subnet
- Private EC2 instances access the internet securely via the NAT Gateway
- Internet Gateway attached to the VPC for public resources

---

### 4️⃣ Security
- **Security Groups** used to control inbound and outbound traffic
- Backend servers only accept traffic from the **private load balancer**
- Frontend servers only expose required ports (HTTP/HTTPS)

---
## Traffic Flow
User
↓
Elastic IP
↓
Public Application Load Balancer
↓
Auto Scaling Group (Frontend EC2s)
↓
Private Application Load Balancer
↓
Backend & Admin EC2s (Private Subnet)


---

## ⚙️ Technologies Used

- **AWS EC2**
- **Auto Scaling Group**
- **Application Load Balancer (Public & Private)**
- **Elastic IP**
- **VPC, Subnets, Route Tables**
- **NAT Gateway**
- **Nginx**
- **Linux (Amazon EC2)**

---

## 📈 Key Cloud Concepts Demonstrated

- High Availability
- Horizontal Scaling
- Private Networking
- Secure Backend Isolation
- Load Balancing
- Real-world AWS Architecture Design

---

## 🧪 Deployment Highlights

- Frontend automatically scales based on demand
- Backend remains protected inside private subnets
- Load balancers distribute traffic efficiently
- Elastic IP ensures stable public access
- NAT Gateway enables secure outbound internet access for private instances

---

## 📌 Future Improvements

- HTTPS using AWS Certificate Manager (ACM)
- CI/CD pipeline using GitHub Actions or AWS CodePipeline
- Containerization with Docker & ECS/EKS
- Monitoring with CloudWatch
- Database integration with RDS

---

## 👨‍💻 Author

**Ayush Dubey**  

---

## ⭐ Why This Project Matters

This project goes beyond basic deployments and reflects **how production systems are actually built on AWS**, making it highly relevant for **cloud engineering and DevOps roles**.
