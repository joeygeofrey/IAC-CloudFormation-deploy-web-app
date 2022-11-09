# Udagram | Web App Deployment

Udagram is a social networking application running on the AWS infrastructure. This CloudFormation template deploys the necessary network and server infrastructure for the Udagram application.

## Project Scope

Your company is creating an Instagram clone called Udagram. Developers want to deploy a new application to the AWS infrastructure. You are now tasked with provisioning the required infrastructure and deploying the latest contibution files from a public S3 bucket onto an Apache Web Server, running on an EC2 instance along with necessary supporting software. The deployment must be automated so that the infrastructure may be discarded immediately after the testing team finishes their test and gather results.

## Deliverables

Diagram: You'll start with a architecture diagram that visually describes your infrastructure and your CloudFormation template.

CloudFormation Template: Interpret the diagram and develop a matching CloudFormation Template with necessary scripts.

### Udagram Architecture Diagram

<img src="/udagram-infra-diagram.png">

### Server Specifications for the Launch Configuration

```sh
* 4 servers, 2 servers placed within each private subnet 
* 2 vCPU minimum
* 4GB RAM minimum
* OS Ubuntu 18 or higher
* 10GB Disk Storage
```

### Security Groups and Roles

