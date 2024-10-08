---
id: 1727975654-lab-2---google-cloud-fundamentals-core-infrastructure
aliases:
  - "LAB 2 - Google Cloud Fundamentals: Core Infrastructure"
tags:
  - google
  - cloud
  - course
  - notes
---

# LAB 2 - Google Cloud Fundamentals: Core Infrastructure

Overview of Google Cloud

## Learning Objectives

1. Define how infrastructure is organized and controlled in Google Cloud.
2. basic infrastructure in Google Cloud.
3. Select and use Google Cloud storage options.
4. Describe the purpose and value of Google Kubernetes Engine.
5. Identify the use cases for serverless Google Cloud services.
6. And combine Google Cloud knowledge with prompt engineering to improve Gemini responses.

## What is Cloud computing?

is a way of using it that has these dive equallt important traits

- on demand and self service
- Access from anywhere
- allocation of resources
- elastic - flexible - scalable
- pay only for what you use

three waves of cloud computing

1. Colocation

- financial efficency of renting physical space intead of investing in data center real estate

2. Virtualized Data Centers

- the components of vdc match the physical building blocks of hosted computing -- severs, cpus, disk, load balancers... but they are virtualized
- virtualized means that the physical resources are not used directly, but rather are used as a service.

3. third

- Virtulization couldnt move fast enough, so google switched to a container-based architecture
- containers are lightweight, portable, and self-contained
- the difference between a container and a virtual machine is that a container is a standardized unit of software that can be run on any host that has the container engine installed.
- Add more flexibility to your applications and infrastructure by using containers.

## IaaS and PaaS

- IaaS

  - on demand infrastructure resources via cloud
  - raw compute, storage network capabilities
  - compute engine (virtual machine) is an example of IaaS

- PaaS
  - bind co to libraries that probvice access to the infra
  - app engine is an example of PaaS
- Serverless
- eliminate the need for any infra management
- Cloud functions
- Cloud Run

- SaaS
  - Gmail, Google Drive, Google Docs, are examples of SaaS

## GC network

- 121 zones in 40 regions
- a zone is where the resources are locate
