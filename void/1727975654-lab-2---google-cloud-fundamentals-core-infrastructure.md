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

# Resources and Access in the Cloud

## Google Cloud resource hierarchy

![Google Cloud Hierarchy](/files/gc-hierarchy.png) 

  structure

1. resources
2. projects
3. folders
4. organization node

### Resources
Resources: vm, buckets bigquery tables, resources.
are organized into projects
projects gan be organized into folders
organization organize all others


policy for each structure
policys have a inheritance chain

### Projects
Projects are the base for use gc services, like managing apis, billing, and managing resources.
projects are separates entities under the organization node
projects hold resources that belongs just to that project
projects can be assign to differents ownes and users and are billing separetly

Each projects have three attributes
  - projects id
    - globally unique
    - assigned by gc but mutable during creation
    - inmutable after creation
  - project name
    - not be unique
    - chosen by user
    - mutable
  - project number
    - globaly unique
    - assigned by gc
    - inmutable

### folders

the resources in a folder inherit policies and permissions assigned to that folder
folder can contain projects other folders ot both

folder are used to group projects under some hierachyt
folder is a great way to mmanage permissions and policies on differentes projects at the same time

### organization node

org poilc administrator
project creator
top level management on users and groups

## Identuty and Acces Management (IAM)

organice who have access to


**WHO** can do **WHAT** and on **WHICH** resources  

- who: google groups, a service account or a cloud identity domain, is also called principal, each principal have an identifier like a email address
- what: is defined by a role, an IAM role is a colletion of permissions
- where: 

> we can deny policies to avoid inherit the premissions for one specific project or folder

basic roles include owner, editor, vewer and billing admin

![GC Roles](/files/gc-roles.png)

predefined roles are a way to custommice roles for a more specific control of permissions and policies, and have predefined actions 

custom roles is the more flexible and customizable for a even more specific control

> [!NOTE]
> a custom role can only be applied to project level or organization level, cant be applied to folder level

## Service account

define permissions to a service rather than a person to control that service, like giving permissions to a compute engine vm.

## Cloud identiy

Google admin console can manage the people on the organization in a more controlled way

## INTERACTING WITH gc

1. Google Cloud console
  - Web based graphical UI
2. Cloud SDK and Cloud Shell
  - google cloud cli
  - bq
  cloud shell are a berowser console 
3. APIs
  - libraries from google API client libraries 
4. Google Cloud app
  - mobile
  - allow start top and use ssh connections
  - is a way to view the resources but does not offer a easy way to manage


# Virtual Machines and Network in the Cloud

## Virtual Private Cloud networking

A VPC network is a private environment that is safe and is isolated. Is hosted in a public cloud and combine the security 

is a way to connect resources in the cloud securely and privately

gogle vpc networks are global
can have subnets, which is a segmented piece of the larger network and can be assigned to any gc **region** 

## Compute Engine

can create and run virtual machiones

a vm can run linux and windows server images, also can build and run images of others os
there are a marketplace wich offers solutions to 

### billing
for the use a vm, compute engine bill by seconds with a one minute minimum, then add discounts for longer runs
for each vm taht runs more than 25% a month, CE applies disconuunt for every additional minute

### preemtible and spot vms

this vm are different that a compute engine vm in that they are preemtible and can be stopped and restarted manually, this can save money.


## Scaling virtual machines

autoscaling

## Important VPC compatibilities



## Cloud Load Balancing

distrubite traffic across multiple instances
single and cross-region load balancing, including automatic multi-region failovers
### use cases

- cross-regional LB for a web app -> globla https load blaancing
- secure sockets layer (ssl) that is not https, global ssl proxy load balancer
- other tcp traffic that doesnt use ssl, global tcp proxy load balancer
- regional external
- regional internal
- cross-region internal

## Cloud DNS and Cloud CDN



## Connecting networks to a Google VPC

cloud vpn -> cloud router to make connection dynamic
use the border gateway protocol
have security concerns

direct peering -> router in the same public datacenter

carrier peering -> direct access from a on premises network through service provider
not covered by a google service leven agreement

dedicated interconnect -> one or more direct, private connections to google

parner interconnect -> useful if data center is in pysycal location that cant reach a dedicated interconnect
if dont warrant an entire 1-0 0ggb per second connection
con be configued to support mission-critical services or apps tha ca tolerate some downtime

cross-cloud interconnect -> connects two or more cloud providers

# Storage in the Cloud

## Google Cloud storage options

## Cloud storage

## Cloud Storage: Storage classes and data transfer

## Cloud SQL

## Spanner

## Firestore

## Bigtable

## Comparing storage options

# Containers in the Cloud

## Introduction to containers

## Kubernetes

## Google Kubernetes Engine

# Applications in the Cloud

## Cloud Run

Cloud run is a servlerless compute engine that can run a container image and scale it up and down
have the cloud functions that are a servlerss execution of a function that can be triggered by events

## Development in the cloud

# Prompt Engineering

### Types of prompt 

![types of prompts](/files/gc-prompt1.png) 
![types of prompts](/files/gc-prompt2.png) 

### Structure of a prompt
![types of prompts](/files/gc-prompt3.png) 




