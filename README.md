# 🌍 Travel Memory Application Deployment

This repository contains the deployment guide for the **Travel Memory Application**, a full-stack web app that allows users to document, share, and revisit their travel memories.

## 📁 Project Repository

Access the full source code here:  
🔗 [https://github.com/UnpredictablePrashant/TravelMemory](https://github.com/UnpredictablePrashant/TravelMemory)

---

## 🎯 Objective

The main goals of this deployment are:

- Set up the backend server built using **Node.js**.
- Configure and deploy the frontend developed with **React**.
- Ensure smooth interaction between frontend and backend.
- Deploy the entire application on an **EC2 instance**.
- Create multiple application instances to enable **load balancing**.
- Integrate a **custom domain** using **Cloudflare** for secure access.

---

## 🛠️ Tasks

### 1. Backend Configuration

- Clone the repository and navigate to the `backend/` directory.
- The backend is configured to run on **port 3000**.
- Use **Nginx** as a reverse proxy to manage HTTP requests and ensure smooth traffic flow on EC2.
- Update the `.env` file with:
  - MongoDB or relevant database connection string
  - Application port (default: `3000`)

First, launch the backend named “Shakti-tm-Backend1”  having ubuntu as a base image, t2.micro as Instance type
## 📷 Screenshots 

![image](https://github.com/user-attachments/assets/d2c73863-8ed1-4092-8071-394c89d46ff2)


---
## Deployment

Installing the Nodejs 18 and git and cloned the git repository of TravelMemory application.

```bash
sudo apt update && sudo apt upgrade -y
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs git
sudo git clone https://github.com/UnpredictablePrashant/TravelMemory.git
```
## 📷 Screenshots 

![image](https://github.com/user-attachments/assets/54589ef1-493d-43f8-80e8-18ac5e17fc7a)



---

## Add database MongoDB credentials in .env by nano .env
```bash
MONGO_URI='mongodb+srv://shaktiranjanm827:X7fe2LuFrLpNE8ND@cluster0.yf0dx.mongodb.net/travelmemory'
PORT=3000
```
## 📷 Screenshots 

![image](https://github.com/user-attachments/assets/94003df7-8123-431e-93b8-424a53752e79)




---
## Install the node application
```bash
cd TravelMemory/backend
npm install 
```
## Start the backend at port 3000
```bash
node index.js
```
## 📷 Screenshots 

![image](https://github.com/user-attachments/assets/8e184642-8745-4f18-a910-1edcda1ca634)


---
## Install nginx 
```bash
sudo apt install nginx
sudo systemctl status nginx 
```
## Screenshots

![image](https://github.com/user-attachments/assets/bb8d488c-0e63-4cb1-9d29-3baf406d1aef)

---

## Setup NGINX Reverse Proxy 
```bash
sudo nano /etc/nginx/sites-available/default
```
-In server block, add: 
```bash
server(
listen 80;
server_name_;
location/{
proxy_pass http:localhost:3000;
}
}
```
## Screenshots
![image](https://github.com/user-attachments/assets/c0e16823-0b20-4143-b91b-caf4fcf83ab9)

---

## Access the backend at port 80 after reverse proxy
![image](https://github.com/user-attachments/assets/40f6ffa4-6e4d-412f-a542-dd37a6494d75)

---

##  Connection of Frontend and Backend:
- First lunch an another instace named 'Shakti-tm-Frontend1'
- Navigate to the `urls.js` in the frontend directory.
- Update the url.js file with the backend IP address

## Launching the frontend named ubuntu as a base image, t2.micro as Instance type
## Screenshots
![image](https://github.com/user-attachments/assets/b3c30ccc-8d15-4962-9b1a-7690bd1e2dc7)

---

## Install Node.js, git, and nginx
```bash
sudo apt update 
sudo apt install -y nodejs nginx git
```
## Screenshots
![image](https://github.com/user-attachments/assets/83ab6a6a-1539-481e-8c5e-d5698228a5a0)
![image](https://github.com/user-attachments/assets/0dfe7838-5a5c-4239-a281-9dc765586335)

---
## Clone the Repo & Build React App
```bash
git clone https://github.com/UnpredictablePrashant/TravelMemory.git
cd TravelMemory/frontend
npm install
```

## update the url.js file with the backend IP address
![image](https://github.com/user-attachments/assets/9151d394-18f0-4b96-835c-437927ee525c)

## Running the application at port 3000 
```bash
sudo npm start   
```
## Screenshots
![image](https://github.com/user-attachments/assets/903af114-33e2-4d5d-b5a6-ff58fae70f72)
![image](https://github.com/user-attachments/assets/38159cb3-a46c-445a-a3b1-99cc0567284d)


---

## The instance's IP address changed after it was stopped.
- Private IP for frontend: 172.31.7.70   
- Public IP for frontend: 3.111.36.30 
- Private IP for backend: 172.31.13.117
- Public IP for backend: 13.201.75.234

## After doing the reverse proxy, the frontend will be running at port 80

## Screenshots
![image](https://github.com/user-attachments/assets/06a783bf-5c4f-47ee-af51-c50dea88f3e2)

---

## Load balancer to handle the traffic
- Create multiple instances of both the front-end and backend servers.
- Add these instances to a load balancer to distribute incoming traffic.

## Creating AMI's for both frontend and backend

## Screenshots
![image](https://github.com/user-attachments/assets/99f431a6-fa0c-4ec7-bd1e-cc8d81080cb4)
![image](https://github.com/user-attachments/assets/3e11eea0-062c-428e-ab0c-e418c3a876d3)
![image](https://github.com/user-attachments/assets/c0f611b5-7f97-40ac-8267-abb72834e50b)
![image](https://github.com/user-attachments/assets/7b63ba3c-0b0f-4221-86e7-a720590e59ca)
![image](https://github.com/user-attachments/assets/c3f2f37b-368b-4261-818c-f228948b7a51)
![image](https://github.com/user-attachments/assets/8f9d2b02-f63a-4580-8150-76a0d56152fb)

## Creating target group for frontend
- EC2 > Target groups > Create target group

 ## Screnshoot
 ![image](https://github.com/user-attachments/assets/7bfcfe8f-ea62-4ef3-acc9-268c779b4e16)
 ![image](https://github.com/user-attachments/assets/009c7d86-6c93-4ecd-a63f-75081a045066)
 ![image](https://github.com/user-attachments/assets/612b1122-088c-4235-af8f-cf007b7f1af6)

---
 
 
 
 ## Create the application load balancer based on the target group
 - EC2 > Load balancers > Create Application Load Balancer

## Screenshots
![image](https://github.com/user-attachments/assets/82037c63-2ed9-482f-ae52-5b3990d20bc5)
![image](https://github.com/user-attachments/assets/6cc47d90-02de-4322-8e0f-3bde0d9b3cb7)
![image](https://github.com/user-attachments/assets/e11c9949-c210-4265-aa0d-4266c9ad3c18)




## Create target group for backend 
- EC2 > Target groups > Create target group

 ## Screnshoot
 ![image](https://github.com/user-attachments/assets/88686ae0-695b-4472-9fb5-813e5e7b72d3)
 ![image](https://github.com/user-attachments/assets/a3623098-7b81-4c37-bfec-ca6f2ea80b2a)
 ![image](https://github.com/user-attachments/assets/fc209de6-bf5b-4641-ac7e-9622e13c0eb7)

---



 ## Create the application load balancer based on the target group
- EC2 > Load balancers > Create Application Load Balancer

## Screenshots

![image](https://github.com/user-attachments/assets/13d9cf6a-9aad-4be0-83dd-9cd1a5b1fc6e)
![image](https://github.com/user-attachments/assets/b47cacce-f723-4318-896a-669cd3b781c2)
![image](https://github.com/user-attachments/assets/ef595105-13f5-498d-9495-85086b21d202)


### Both the Load Balancers are active

![image](https://github.com/user-attachments/assets/09234b8d-027c-4ddb-b38a-397466d1ff48

## DNS 
- DNS of backend load balancer- Shakti-lb-backend-471755778.ap-south-1.elb.amazonaws.com
- DNS of frontend load balancer- Shakti-lb-frontend-1826694796.ap-south-1.elb.amazonaws.com


### Put the backend load balancer's DNS in frontend's url.js 

![image](https://github.com/user-attachments/assets/fcdd7072-ae8d-437a-b84d-cfaab044b341)

---
### Now open your Frontend Load Balancer DNS in the browser

![image](https://github.com/user-attachments/assets/95e16588-717b-4069-9756-1b9e802ef60f)





 
  - 


















