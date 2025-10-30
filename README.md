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
