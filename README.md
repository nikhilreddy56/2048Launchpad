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
<img width="1122" height="247" alt="Screenshot 2025-10-30 152308" src="https://github.com/user-attachments/assets/0498c8cd-5eab-422a-a2be-a874e7039546" />

