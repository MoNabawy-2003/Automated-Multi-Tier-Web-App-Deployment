# 🚀 vProfile: Automated Multi-Tier Web App Deployment

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Build](https://img.shields.io/badge/Build-Maven-blue)
![Platform](https://img.shields.io/badge/Platform-Linux%20%7C%20Vagrant-lightgrey)

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Architecture](#-architecture)
- [Prerequisites](#-prerequisites)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [How to Run (One-Click Deployment)](#-how-to-run-one-click-deployment)

---

## 📖 Project Overview
**vProfile** is a complex, multi-tier Java web application simulating a real-world social networking platform.
The goal of this project is to shift from a **Manual Provisioning** approach (prone to errors and slow) to an **Automated Infrastructure as Code (IaC)** approach using **Vagrant** and **Bash Scripting**.

This setup automatically provisions **5 Virtual Machines**, installs all dependencies, configures services, and deploys the application artifact in under **15 minutes**.

---

## 🏗 Architecture
The application runs on a distributed system consisting of 5 distinct services:

| VM Name | Service | Role | IP Address |
| :--- | :--- | :--- | :--- |
| **web01** | Nginx | Load Balancer & Reverse Proxy | `192.168.56.11` |
| **app01** | Tomcat | Application Server (Java Spring) | `192.168.56.12` |
| **db01** | MySQL | Relational Database | `192.168.56.15` |
| **mc01** | Memcached | Database Caching Service | `192.168.56.14` |
| **rmq01** | RabbitMQ | Message Broker Agent | `192.168.56.16` |

> **Request Flow:** `User` -> `Nginx` -> `Tomcat` -> `MySQL` (Cached by `Memcached` & Queued by `RabbitMQ`).

---

## 🛠 Tech Stack
* **OS:** CentOS 7 (Backend Services), Ubuntu (Web Layer).
* **Virtualization:** Oracle VirtualBox.
* **Automation:** Vagrant (IaC) & Bash Scripting.
* **Web Server:** Nginx.
* **App Server:** Apache Tomcat.
* **Database:** MariaDB (MySQL).
* **Build Tool:** Apache Maven.

---

## ⚙ Prerequisites
Before running the project, ensure you have the following installed:
1.  [Oracle VirtualBox](https://www.virtualbox.org/)
2.  [Vagrant](https://www.vagrantup.com/)
3.  [Git](https://git-scm.com/)
4.  Git Bash (for Windows users)

---

## 📂 Project Structure
The automation logic is modularized into separate scripts for each tier:

```bash
├── Vagrantfile             # Defines VM specs (RAM, CPU, IPs)
├── scripts/
│   ├── mysql.sh            # DB setup & Dump Restore
│   ├── memcache.sh         # Caching setup
│   ├── rabbitmq.sh         # Broker setup
│   ├── tomcat.sh           # Java setup, Maven Build & Deploy
│   └── nginx.sh            # Reverse Proxy Config
└── src/                    # Java Source Code

```

---

## 🕹️ How to Run (One-Click Deployment)

### Step 1: Clone the Repository

```bash
# Clone the repository to your local machine
git clone https://github.com/MoNabawy-2003/Automated-Multi-Tier-Web-App-Deployment.git

# Navigate into the project directory
cd Automated-Multi-Tier-Web-App-Deployment

```

### Step 2: Launch Infrastructure

```bash
# Execute the main automation command to build the stack
vagrant up

# -----------------------------------------------------------
# NOTE: 
# This command triggers the creation of all 5 Virtual Machines.
# It will download OS images and run the provisioning scripts.
# Estimated time: 10-30 minutes (depending on internet speed).
# -----------------------------------------------------------

```

### Step 3: Verify & Access

```bash
# 1. Check the status of the machines to ensure they are 'running'
vagrant status

# 2. Access the application in your browser at:
# URL: http://192.168.56.11
# (You should see the vProfile Login Page)

```
