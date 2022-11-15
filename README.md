# Udagram | Web App Deployment - Joey Geofrey

Udagram is a web application running on the AWS infrastructure. This CloudFormation template deploys the necessary network and server infrastructure for the Udagram application.

## Project Scope

Your company is creating an Instagram clone called Udagram. Developers want to deploy a new application to the AWS infrastructure. You are now tasked with provisioning the required infrastructure and deploying the latest contibution files from a public S3 bucket onto an Apache Web Server, running on an EC2 instance along with necessary supporting software. The deployment must be automated so that the infrastructure may be discarded immediately after the testing team finishes their test and gather results.

## Deliverables

Diagram: An architecture diagram that visually describes your infrastructure and your CloudFormation template.

CloudFormation Template: Interpret the diagram and develop a matching CloudFormation Template with necessary resources.

### Network Specifications for the Udagram Web Application

```sh
* 2 availability zones within the VPC to ensure continuous high availability
* 2 public subnets with NAT gateways to route traffic to web app instances
* 2 private subnets containing the web app instances and private route tables
* Application load balancer to equally provsion traffic into the web app
* Auto scaling group to ensure scalability of the web app instances
* Security groups with appropriate inbound/outbound configurations
* Bastion host to access and troubleshoot the web app instances - dedicated ASG group to ensure high availability
```

### Server Specifications for the Udagram Web Application

```sh
* 4 servers, 2 servers placed within each private subnet 
* 2 vCPU minimum
* 4GB RAM minimum
* OS Ubuntu 18 or higher
* 10GB Disk Storage
```

### Udagram Architecture Diagram

<img src="/udagram-infra-diagram.png">

## Udagram Architecture Deployment

For a successful stack deployment, ensure that you have the latest AWS CLI configured. AWS CLI [installation documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions "AWS Command Line Interface").

### Instructions for Udagram Network

```sh
./create.sh UdagramNetwork udagram-network.yml udagram-network.json
```

### Instructions for Udagram Servers

```sh
./create.sh UdagramServer udagram-servers.yml udagram-servers.json
```

### Instructions for Udagram Stack Deletion

```sh
./delete.sh UdagramServer
```
followed by 

```sh
./delete.sh UdagramNetwork
```