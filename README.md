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








