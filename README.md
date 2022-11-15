# Udagram | Web App Deployment - Joey Geofrey

Udagram is a web application running on the AWS infrastructure. This CloudFormation template deploys the necessary network and server infrastructure for the Udagram application.

## Project Scope

Your company is creating an Instagram clone called Udagram. Developers want to deploy a new application to the AWS infrastructure. You are now tasked with provisioning the required infrastructure and deploying the latest contibution files from a public S3 bucket onto an Apache Web Server, running on an EC2 instance along with necessary supporting software. The deployment must be automated so that the infrastructure may be discarded immediately after the testing team finishes their test and gather results.

## Deliverables

Diagram: An architecture diagram that visually describes your infrastructure and your CloudFormation template.

CloudFormation Template: Interpret the diagram and develop a matching CloudFormation Template with necessary resources.

### General Specifications for the Udagram Web Application

```sh
* 2 availability zones within the VPC to ensure continuous high availability
* 2 public subnets with NAT gateways to route traffic to web app instances
* 2 private subnets containing the web app instances and private route tables
* Application load balancer to equally provsion traffic into the web app
* Auto scaling group to ensure scalability of the web app instances
* Security groups with appropriate inbound/outbound configurations
* Bastion host to access and troubleshoot the web app instances
* Dedicated Bastion ASG to ensure high availability
* S3 bucket to download application archive
* IAM role that allows web app instances to use S3 services
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

## Udagram Stack Deployment

For a successful stack deployment, ensure that you have the latest AWS CLI configured. Access the AWS CLI [installation documentation](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html#getting-started-install-instructions "AWS Command Line Interface"). You will also require execute permissions to successfully run the create/delete shell scripts.

### Grant execute permissions for Shell Scripts

```sh
chmod +x create.sh
chmod +x delete.sh
```

### Deploying the Udagram Network

```sh
./create.sh UdagramNetwork udagram-network.yml udagram-network.json
```

### Deploying the Udagram Servers

```sh
./create.sh UdagramServer udagram-servers.yml udagram-servers.json
```

## Udagram Stack Deletion

We will start off by deleting the server stack, followed by the network stack. Deletion of the network stack requires deletion of server components.

### Deleting the Udagram Servers

```sh
./delete.sh UdagramServer
```
### Deleting the Udagram Network

```sh
./delete.sh UdagramNetwork
```