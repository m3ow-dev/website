---
title: Immortal Hosting
description: Inside the architecture of immortal.host
slug: immortal-host
date: 2025-07-30 00:00:00+0000
tags:
 - immortal.host
---

## Introduction

[Immortal Hosting](https://immortal.host) is a high-performance infrastructure project built on modern DevOps practices. More than just a hosting provider, it is a self-managed ecosystem leveraging container orchestration, edge computing, and high-availability clusters to deliver resilient application and game server hosting.

## Leadership & Architecture

As **Founder and Lead Architect**, I manage the lifecycle of the entire platform—from the metal up to the frontend. My focus includes:

* **Strategic Architecture:** Designing cloud-agnostic, containerized infrastructure that scales from single nodes to distributed clusters.
* **Full-Stack Development:** Building reactive interfaces with Next.js and integrating them with backend game protocols.
* **DevSecOps:** Enforcing a Zero Trust mindset with rootless containers and centralized identity management.
* **Operations:** Handling everything from database tuning to disaster recovery protocols.

## Infrastructure & Orchestration

We moved beyond simple bare-metal deployments to a fully orchestrated environment.

* **Kubernetes (K8s):** The control plane. We use custom YAML configurations to orchestrate complex workloads, ensuring high availability for databases and control panels.
* **Rootless Podman:** Used for granular security. Running containers without root privileges significantly reduces the attack surface while maintaining OCI compliance.

## CI/CD & Automation

Code moves from development to production through a strict, automated pipeline.

* **Managed Private Gitea:** Our central hub for version control, hosting both application source code and Infrastructure-as-Code (IaC).
![Git](git.png)
* **CI/CD Runners:** Automated runners handle testing, building, and deployment directly to the Kubernetes clusters, ensuring rapid and consistent delivery.

## Security & Identity

Security isn't an afterthought; it's the foundation.

* **Authentik (SSO):** A unified identity layer. **Authentik** acts as the central Identity Provider (IdP), enforcing strict access policies and providing Single Sign-On across all internal tools.
![Auth](auth.png)
* **Zero Trust Networking:** By combining strict routing with trusted proxies, origin servers remain obfuscated and protected from direct internet exposure.

## Data & Game Management

We prioritize data integrity and low-latency performance for gaming workloads.

* **Database & Backups:** We utilize **MariaDB** in a high-availability cluster. For safety, we enforce continuous automated offsite S3 backups.
* **Pelican Panel:** A modern, open-source interface for deploying and managing game server instances.
![Panel](panel.png)

## Networking Stack

Speed and security are balanced using a modern reverse proxy architecture.

* **Cloudflare Integration:** Sitting in front of the stack, Cloudflare provides edge caching, DNS management, and critical DDoS protection against Layer 3/4 and Layer 7 attacks.

## Operations & Web

* **Monitoring:** We track infrastructure health in real-time. Automated systems monitor server metrics, container status, and network latency.
![Monitoring](monitoring.png)
* **Support:** As a founder-led project, support is technical and responsive, bridging the gap between complex infrastructure and user needs.
![Status Page](status.png)
* **Frontend:** The public-facing web properties are built with **Next.js (React)**, allowing for dynamic, multi-language content.
![Main Website](website.png)

---

## Tech Stack Summary

| Category | Technology |
| :--- | :--- |
| **Role** | **Founder & Lead Architect** |
| **Orchestration** | Kubernetes, Docker Compose, Rootless Podman |
| **DevOps / CI/CD** | Private Gitea + Runners |
| **Authentication** | Authentik (SSO/IdP) |
| **Database** | MariaDB HA Cluster | 
| **Network Security** | Cloudflare (DDoS Protection, DNS) |
| **Game Control** | Pelican Panel |
| **Frontend** | Next.js (React) |
