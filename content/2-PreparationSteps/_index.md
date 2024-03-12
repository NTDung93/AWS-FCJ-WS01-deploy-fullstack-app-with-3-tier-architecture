---
title : "Preparation Steps"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

## Firewall in VPC

In this section, we will learn about the basic security features in Amazon VPC, such as the Security Group firewall feature and Network Access Control Lists.

### Security Groups

A **Security Group** acts as a virtual firewall for an EC2 Instance, allowing control over network traffic. In a VPC, an Instance can be assigned up to 5 Security Groups. It's important to note that Security Groups operate at the Instance layer and not at the Subnet layer.

> **Note:** Security Groups function at the virtual machine level, rather than the subnet level. However, each virtual machine within a subnet can be assigned to different security groups.

### Network ACLs

A **Network Access Control List (ACL)** is an optional security layer for VPCs. It acts as a firewall to manage incoming and outgoing traffic for one or more subnets. Network ACLs can be configured with the same rules as security groups, providing an additional layer of security to the VPC.

### Contents

- [Security Groups](2.1-securitygroup/)
- [Network ACLs](2.2-networkacls/)
