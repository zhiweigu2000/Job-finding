Availability zones: cluster of data centers

Region: cluster of availability zone

Aspects to consider to decide region: compliance, latency, price, service availability

Interaction: AWS management console, AWS command line interface (CLI), AWS software development kits (SDKs)

Shared responsibility model: AWS responsible for security of the cloud (hardware and software), customer responsible for security in the cloud (data)

Amazon machine images: AMI launch EC2 instances, EC2 instances can launch AMI

Electric Compute Cloud (EC2): combination of virtual processors (vCPUs), memory, network, instance staorage and image processing units (GPHs)

EC2 lifecycle:

![image](https://user-images.githubusercontent.com/76275089/148132794-5e80274f-b37c-4b68-bccf-9389aa5db105.png)

Categories of compute: virtual machines, containers, serverless

Container: a standardized unit that packages up code and all its dependencies, run on any platform

Docker: a popular container runtime that simplifies the management of the entire operating system stack needed for container isolation, including networking and storage, easy to create, package, deploy, and run containers

Difference between containers and VMs

![image](https://user-images.githubusercontent.com/76275089/148136011-0203ded0-fcef-44c1-9142-3f50977c85e5.png)

Virtual machines: maintain a copy of an operating system -- cost waste, offer full strength of an operating system and offer more resources

Elastic Container Service (ECS): create new containers and manage across EC2 instances

Elastic Kubernetes Service (EKS): platform for managing containerized workloads and services, run of Kubernetes

ECS and EKS can run on two modes: EC2, AWS Fargate

AWS Fargate: manage the infrastructure, developers focus on application development

AWS Lambda: manage EC2 instances and containers, developers upload code into AWS Lambda, code runs in a isolated environment

Function name: lambda_handler

File name: lambda_function.py

Networking: connect computers and communicate

IP address: 32-bit address

IPv4 address: decimal format, separated by period

CIDR address: IPv4 address/n, n represents how many bits are fixed

VPC: isolated network in AWS Cloud, include name, region (multiple AZ within the region), IP range

Subnet: smaller network inside base network, include VPC, AZ, IP address (subset of VPC), two subnet in two AZ

Main route table: a set of routes that are used to determine where network traffic is directed

Security group: block all inbound traffic, allow all outbound traffic

Put resources into different groups, create security groups for each control network communication between them





