# AWS 3-Tier Architecture

This repository contains an **AWS 3-Tier Architecture** provisioned using **Terraform Infrastructure as Code (IaC)**.

The architecture separates infrastructure into three logical tiers:

1. **Presentation Tier** – Internet-facing Application Load Balancer
2. **Web Tier** - Web Application
3. **Application Tier** – Private EC2 instances
4. **Database Tier** – Private Amazon RDS MySQL

The infrastructure is deployed across multiple Availability Zones to improve availability, fault tolerance, and scalability.

---


The architecture separates components into Presentation, Application, and Database tiers to improve security, scalability, and maintainability.

---

### Networking layer

**Amazon VPC**
A dedicated Virtual Private Cloud (VPC) provides network isolation for all infrastructure component.

VPC CIDR : `10.0.0.0/16`
Region : `ap-south-1`

## Subnet Design

The infrastructure is divided into three subnet tiers across two Availability Zones.

| Subnet Type | CIDR Block | Availability Zone | Purpose | Network Exposure |
| :--- | :--- | :--- | :--- | :--- |
| **Public Subnet 1** | `10.0.0.0/20` | AZ 1 | Application Load Balancer | Public / Internet Facing |
| **Public Subnet 2** | `10.0.16.0/20` | AZ 2 | Application Load Balancer | Public / Internet Facing |
| **Application Subnet 1** | `10.0.32.0/20` | AZ 1 | EC2 Application Server | Private |
| **Application Subnet 2** | `10.0.48.0/20` | AZ 2 | EC2 Application Server | Private |
| **Database Subnet 1** | `10.0.96.0/20` | AZ 1 | Amazon RDS MySQL | Private / Isolated |
| **Database Subnet 2** | `10.0.112.0/20` | AZ 2 | Amazon RDS MySQL | Private / Isolated |

## Architecture Diagram

![3tier-aws-architecturet](architecture/3-tier-aws-architecture.png)