---
title: Immortal Hosting
description: Inside the architecture of immortal.host
slug: immortal-host
date: 2025-07-30 00:00:00+0000
tags:
 - immortal.host
---

## Introduction

[Immortal Hosting](https://immortal.host) is a high-performance infrastructure project built on modern DevOps practices. It is the project I am most proud of—a production infrastructure entirely built on a **three-node on-premise cluster**.

More than just a hosting provider, it is a self-managed ecosystem leveraging **container orchestration**, edge computing, and high-availability clusters to deliver resilient application and game server hosting. This project is a direct reflection of my passion for cloud infrastructure; it is the focus of my continuous learning and development outside of my university studies.

## Leadership & Architecture

As **Founder and Lead Architect**, I manage the lifecycle of the entire platform—from the metal up to the frontend. My focus includes:

* **Strategic Architecture:** Designing cloud-agnostic, containerized infrastructure that scales from my physical nodes to distributed clusters.
* **Full-Stack Development:** Building reactive interfaces with Next.js and integrating them with backend game protocols.
* **DevSecOps:** Enforcing a Zero Trust mindset with containers and centralized identity management.
* **Operations & Reliability:** Maintaining a strict 99.80% SLA, a metric that serves as a direct testament to the reliability of the architecture and my competence in maintaining uptime.

## Infrastructure: The Private Cloud

We moved beyond simple bare-metal deployments to a fully orchestrated private cloud environment running on custom hardware.

* **Physical Network:** The backbone of the cluster is powered by MikroTik hardware, handling high-throughput routing, VLAN segmentation, and hardware-level firewalling to ensure low-latency connectivity between nodes.
* **OpenStack:** We utilize OpenStack as our Infrastructure-as-a-Service (IaaS) layer. It abstracts the physical resources of the 3-node cluster, providing a flexible and scalable private cloud environment to provision virtual resources on demand.

## Orchestration & Containerization

The core philosophy of Immortal Hosting is "Everything as a Container."

* **Kubernetes (K8s):** Sitting on top of our OpenStack layer, Kubernetes acts as the primary control plane. We use custom YAML configurations to orchestrate complex workloads, ensuring high availability (HA) for databases and control panels.
* **Containerization Strategy:** All services are strictly containerized. This decouples applications from the underlying OS, ensuring consistency across development, testing, and production environments.

## IaC & Automation

Manual configuration is replaced by code. We adhere strictly to **Infrastructure as Code (IaC)** principles to maintain state and reproducibility.

* **Ansible:** We use Ansible for configuration management and node provisioning. It automates the setup of the underlying OS, network interfaces, and dependencies, ensuring that our infrastructure is idempotent and easily recoverable.

* **Managed Private Gitea:** Our central hub for version control, hosting both application source code and our IaC repositories.
![Git](git.png)
* **CI/CD Runners:** Automated runners handle testing, building, and deployment directly to the Kubernetes clusters, ensuring rapid and consistent delivery.

## Security & Identity

Security isn't an afterthought; it's the foundation.

* **Authentik (SSO):** A unified identity layer. Authentik acts as the central Identity Provider (IdP), enforcing strict access policies and providing Single Sign-On across all internal tools.
![Auth](auth.png)
* **Zero Trust Networking:** By combining strict routing with trusted proxies, origin servers remain obfuscated and protected from direct internet exposure.

## Data & Game Management

We prioritize data integrity and low-latency performance for gaming workloads.

* **Database & Backups:** We utilize MariaDB in a high-availability cluster. For safety, we enforce continuous automated offsite S3 backups.
* **Pelican Panel:** A modern, open-source interface for deploying and managing game server instances.
![Panel](panel.png)

## Networking Stack

Speed and security are balanced using a modern reverse proxy architecture.

* **Cloudflare Integration:** Sitting in front of the stack, Cloudflare provides edge caching, DNS management, and critical DDoS protection against Layer 3/4 and Layer 7 attacks.

## Operations & Web

* **Monitoring:** We track infrastructure health in real-time. Automated systems monitor server metrics, container status, and network latency.
![Monitoring](monitoring.png)
* **Status:** As a founder-led project, support is technical and responsive, bridging the gap between complex infrastructure and user needs. Our uptime status page shows clearly our dedication to keeping our client's services online at (almost) all times.
![Status Page](status.png)
* **Frontend:** The public-facing web properties are built with Next.js (React), allowing for dynamic, multi-language content.
![Main Website](website.png)

---

## Tech Stack Summary

| Category | Technology |
| :--- | :--- |
| **Role** | **Founder & Lead Architect** |
| **Infrastructure** | 3-Node On-Prem Cluster |
| **Networking Hardware** | MikroTik |
| **Private Cloud** | OpenStack |
| **Orchestration** | Kubernetes, Docker Compose, Rootless Podman |
| **Configuration Mgmt** | Ansible (IaC) |
| **DevOps / CI/CD** | Private Gitea + Runners |
| **Authentication** | Authentik (SSO/IdP) |
| **Database** | MariaDB HA Cluster | 
| **Network Security** | Cloudflare (DDoS Protection, DNS) |
| **Game Control** | Pelican Panel |
| **Frontend** | Next.js (React) |
| **Reliability** | 99.80% SLA |