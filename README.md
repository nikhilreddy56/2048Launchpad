# Docker-project

# 🧩 2048 Game Docker Deployment Guide

This repository demonstrates how to **containerize** a simple 2048 web game using Docker, **build and run it on an Ubuntu server**, and finally **push the image to AWS Elastic Container Registry (ECR)** for deployment.

---

## 🚀 Prerequisites

Before you begin, ensure the following tools are installed on your Ubuntu server:

```bash
sudo apt update -y
sudo apt install -y docker.io awscli git
sudo systemctl start docker
sudo systemctl enable docker

🧱 Step 1: Create a Dockerfile

In the project root directory, create a file named Dockerfile:

FROM ubuntu:22.04

RUN apt-get update
RUN apt-get install -y nginx zip curl

RUN echo "daemon off;" >>/etc/nginx/nginx.conf
RUN curl -o /var/www/html/master.zip -L https://codeload.github.com/gabrielecirulli/2048/zip/master

RUN cd /var/www/html/ && unzip master.zip && mv 2048-master/* . && rm -rf 2048-master master.zip
EXPOSE 80
CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]

🏗️ Step 2: Build the Docker Image

Build the Docker image and tag it with a name and version:
docker build -t 2048-game:latest .

Verify the image:
docker images

You should see something like:
<img width="1124" height="247" alt="Image" src="https://github.com/user-attachments/assets/9e658801-88e1-46aa-976f-f7b88cfc9e24" />

🧩 Step 3: Run the Container

Run the game locally on port 80:
docker run -d -p 80:80 2048-game:1.0

Verify the container is running:
docker ps

Access the game in your browser using your server’s public IP:
http:http://52.91.92.185:80/

You should see the 2048 game running 🎮 (PS:Here I used port 90)

<img width="1316" height="671" alt="image" src="https://github.com/user-attachments/assets/f5cc0170-800f-4a51-b01d-537a60b9d46d" />


