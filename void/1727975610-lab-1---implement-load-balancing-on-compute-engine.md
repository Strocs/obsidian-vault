---
id: 1727975610-lab-1---implement-load-balancing-on-compute-engine
aliases:
  - LAB 1 - Implement Load Balancing on Compute Engine
tags:
  - google
  - cloud
  - course
  - lab
---

# LAB 1 - Implement Load Balancing on Compute Engine

## Create a VM through gcloud console

`gcloud compute instances create [INSTANCE_NAME]`
`gcloud compute instances create [name] --machine-type e2-medium --zone $ZONE`

- Connect to vm via ssh
  `gcloud compute ssh [name] --zone $ZONE`

## Regions and Zones

- Set the region to us-west1
  `gcloud config set compute/region us-west1`

- View the project region setting
  `gcloud config get-value compute/region`

- Set the zone to us-west1-c
  `gcloud config set compute/zone us-west1-c`

- View the project zone setting
  `gcloud config get-value compute/zone`

## Environment variables

- Environment variables define your environment and help save time when you write scripts that contain APIs or executables.

- Create an environment variable to store your Project ID:
  `export PROJECT_ID=$(gcloud config get-value project)`

- Create an environment variable to store your Zone:
  `export ZONE=$(gcloud config get-value compute/zone)`

## Load Balancer

### Network Load Balancer

- Distribute traffic to backends, so when client send a request to de LB it will be routed to the backend with the least amount of requests

### HTTP Load Balancer

- HTTP load balancer uses HTTP as its protocol.

---

> - HTTP load balancer use TCP protocol and network load balancer use UDP protocol
> - TCP protocol is a connection oriented protocol, it is reliable and ordered, but it is not a stream protocol, so it can not be used for file transfer
>   - The most common usage of http load balancer is for web server
> - UDP protocol is a connectionless protocol, it is unreliable and unordered, but it is a stream protocol, so it can be used for file transfer
>   - The most common usage of network load balancer is for database server

---

# LAB WEEK 1 - Challenge

## Task 1. Create a project jumphost instance

You will use this instance to perform maintenance for the project.

Requirements:

- Name the instance Instance name.
- Create the instance in the ZONE zone.
- Use an e2-micro machine type.
- Use the default image type (Debian Linux).

`gcloud compute instances create [INSTANCE_NAME] --zone [ZONE] --machine-type e2-micro`

## Task 2. Set up an HTTP load balancer

You will serve the site via nginx web servers, but you want to ensure that the environment is fault-tolerant. Create an HTTP load balancer with a managed instance group of 2 nginx web servers. Use the following code to configure the web servers; the team will replace this with their own configuration later.

```bash
cat << EOF > startup.sh
#! /bin/bash
apt-get update
apt-get install -y nginx
service nginx start
sed -i -- 's/nginx/Google Cloud Platform - '"\$HOSTNAME"'/' /var/www/html/index.nginx-debian.html
EOF
```

> [!NOTE] There is a limit to the resources you are allowed to create in your project, so do not create more than 2 instances in your managed instance group. If you do, the lab might end and you might be banned.

You need to:

- Create an instance template. Don't use the default machine type. Make sure you specify e2-medium as the machine type and create the Global template.
  `gcloud compute instance-templates create [INSTANCE_TEMPLATE_NAME] --machine-type e2-medium --metadata-from-file startup-script=./startup.sh`

- Create a managed instance group based on the template.
  `gcloud compute instance-groups managed create [INSTANCE_GROUP_NAME] --template [INSTANCE_TEMPLATE_NAME] --size 2 `
  `gcloud compute instance-groups managed set-named-ports [INSTANCE_GROUP_NAME] --named-ports http:80`

- Create a firewall rule named as Firewall rule to allow traffic (80/tcp).
  `gcloud compute firewall-rules create [FIREWALL_RULE_NAME] --allow tcp:80`

- Create a health check.
  `gcloud compute health-checks create [PROTOCOL (http)] [HEALTH_CHECK_NAME] --port 80`

- Create a backend service and add your instance group as the backend to the backend service group with named port (http:80).
  `gcloud compute backend-services create [BACKEND_SERVICE_NAME] --protocol HTTP --port-name http --health-checks [HEALTH_CHECK_NAME] --global`
  `gcloud compute backend-services add-backend [BACKEND_SERVICE_NAME] --instance-group [INSTANCE_GROUP_NAME] --instance-group-zone [ZONE] --global`

- Create a URL map, and target the HTTP proxy to route the incoming requests to the default backend service.
  `gcloud compute url-maps create [URL_MAP_NAME] --default-service [BACKEND_SERVICE_NAME] --global`

- Create a target HTTP proxy to route requests to your URL map
  `gcloud compute target-http-proxies create [TARGET_HTTP_PROXY_NAME] --url-map [URL_MAP_NAME] --global`

- Create a forwarding rule.

  > [!NOTE]
  > To get IP address we can do the following:
  > `gcloud compute addresses create [IP_ADDRESS_NAME] --ip-version IPV4 --global` > `gcloud compute addresses describe [IP_ADDRESS_NAME] --format "get(address)" --global`

  `gcloud compute forwarding-rules create [FORWARDING_RULE_NAME] --address [IP_ADDRESS or IP_ADDRESS_NAME] --global --target-http-proxy [TARGET_HTTP_PROXY_NAME] --ports 80`
