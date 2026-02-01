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
- [Troubleshooting & Challenges](#-troubleshooting--challenges)
- [Author](#-author)

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
1.