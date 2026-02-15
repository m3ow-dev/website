---
title: OpenShift (The Hard Way)
description: My personal experience with OKD and all the things I learnt along the way.
slug: openshift
date: 2025-02-11 00:00:00+0000
weight: 1
tags:
- openshift
- okd
- openstack
---

# The Why, the When, and the How

## The future of Immortal Hosting

### OPENSTACK

When the time came to upgrade and enhance the infrastructure of Immortal Hosting, my colleague and I looked at the different alternatives to orchestrate and deploy our Containers and VMs: we came across Docker Swarm, wanted more reliability and scaling, so we thought of the same thing. Deploying our infrastructure entirely with Kubernetes and some sort of Infrastructure as Code framework to make things easier. Being a fan of RedHat, we looked at what they had to offer. Being the developers and maintainers of Ansible and an opensource cloud platform named OpenStack, we were eager to test this combination of new tools and tech out. I started by reading the entire Architecture Manual of OpenStack, then deployed it "by hand" on VMs, and thought to myself, there must be a better way to do this. I then looked into the different deployment guides of OpenStack itself, stumbling across kolla-ansible. This version of OpenStack is basically an agglomeration of a truck load of Ansible playbooks to setup, configure and deploy your selection of OpenStack components, all while running on Docker (or Podman). Thing is, if you do an error in your configuration, you have to wipe your deployment then re-play all of your Ansible playbooks, or else you get weird MySQL errors and unmet dependencies that were supposed to run before where you resumed your playbook. And while we're at it, I'll talk about MySQL... After a VM restart the containers of all my MySQL instances suddenly were in a boot loop and all mysql-recovery commands gave no hope whatsoever. Not only this, but I tried installing Magnum and Kubernetes on OpenStack Horizon directly, and gosh was that a waste of time before I learnt about Cluster API. Later on in my discoveries I learnt that Heat was being discontinued in favor of Cluster API, and I understand why now. All of these issues led me to put aside the kolla-ansible project and continue researching on some alternatives that are container-centric.

TL;DR, OpenStack as a whole needs years of experience to operate in production and I wasn't ready for this, and isn't suited for our container-only ideology.

### OKD (OPENSHIFT in a nutshell)

I then looked more into the world of RedHat to see what succulent products they offer in terms of container/VM hypervisors. And then came the revelation of OpenShift. This absolute beast of an operating system manages your Kubernetes cluster as if it was a piece of cake, supports virtualization and has quite literally everything you need to operate your private/public cloud. I started out by wiping an entire bare-metal server and creating two VMs for the required 3 control plane nodes requirement of OpenShift. I then looked at the documentation of the community-driven, upstream version of OpenShift, named OKD(.io). At the time I didn't know that the documentation site of OKD is basically a 1-1 clone of the official OpenShift Documentation. I then looked into the installation methods and an overview of what I was going to deal with while setting this monster of a distribution up. I clicked on assisted installer, filled out the fields, and downloaded the compiled boot ISO. After setting everything up and the installation was successful, I am presented with the magnificent message of **"60 DAYS REMAINING OF YOUR TRIAL SUBSCRIPTION"**. I thought to myself, yeah I know why this was so easy after all, I installed the paid version of OpenShift.

### OKD 2.0

Now back to the drawing board. I looked at my options and spent another 8-10 hours finding the best way to install the OKD platform. And now here I am, installing my own OKD on my on-prem infra as the main hypervisor using the agent installation method. All while suffering through the 200kb/s speed of the HP ILO 4 web interface's virtual media mount.

### OKD 2.1 

Turns out Centos10 is no longer supported by the HP ProLiant 360p Gen8, the server literally resets after booting the iso from both ventoy and dd-ing the iso directly on the usb key. So instead of installing it baremetal, we decided to sell this Gen8 and buy something more recent to fix this problem. For now, the OKD cluster is running in VMs on our other two servers which is working flawlessly. It does use about 30 gb of ram idle (over three nodes), which is a bit worrying but the install and upgrade operations to OpenShift 4.21.0-okd-scos.5 was without any headaches. Up until now, i am very happy with OKD's performance and ease of use. It is OpenShift after all, and me, being a RedHat glazer loves to have anything RHEL-related.

I also sumbled across RDO OpenStack which is more promissing in terms of ease of installation than pure vanilla OpenStack. And this line on the CentOS looks very very interesting "With RDO, you can also deploy certain OpenStack Services within an OKD cluster"

To be tested...     