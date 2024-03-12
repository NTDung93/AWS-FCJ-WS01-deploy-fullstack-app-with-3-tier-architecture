---
title : "Create Internal Load Balancer and Auto Scaling Group"
date : "`r Sys.Date()`"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

In this guide, we will discuss how to connect an On-premise data center to Amazon VPC using a hard or soft VPN, depending on the specific requirements. To establish a Site-to-Site VPN connection, the following steps need to be taken:

## 1. Virtual Private Gateway (VPG) and Customer Gateway (CGW) Setup

- **Virtual Private Gateway (VPG)**: This serves as the control center that connects the virtual private network (VPN) within AWS.

- **Customer Gateway (CGW)**: This component represents the hard or soft VPN device located at the Client's end.

## 2. VPN Tunnel Establishment

A VPN tunnel will be initiated as soon as data traffic is exchanged between AWS and the client's network. It is important to specify the routing type to ensure secure and efficient data transmission:

- If the CGW on the client side supports Border Gateway Protocol (BGP), dynamic routing should be configured for the VPN connection.

- If not, static routing must be set up. For static routing, specific routes must be entered to establish the connection from the client's side to the VPG at AWS. Additionally, the VPC routing must be configured to allow seamless data exchange within the VPN tunnel.

## 3. VPG, CGW, and VPN Features

Some key features of VPG, CGW, and VPN include:

- **VPG**: The terminal component of the VPN tunnel within AWS.

- **CGW**: Can be either a hardware device or a software application located at the Client's end in the VPN tunnel.

- VPN tunnel connections are initiated from CGW to VPG.

- VPG supports both dynamic routing (BGP) and static routing.

- Each VPN connection comprises two tunnels for high availability.

## 4. Lab Setup and Configuration

The lab provides hands-on experience in setting up a Site-to-Site VPN connection in AWS. This solution is popular due to its cost-effectiveness and ease of configuration, as AWS offers instructions for various types of client devices. The primary responsibility of the customer is to prepare the internet connection, which will establish a secure tunnel (using IPSec) connecting to AWS via the VPN tunnel.

In the lab scope, there are two VPCs: the Main office (VPC **ASG**) and the Branch office (VPC **ASG VPN**), located in different Availability Zones (AZs) to ensure network diversity. While EC2 instances can be created in each VPC with external SSH access, they cannot communicate or ping each other using private IP addresses. The goal is to configure the VPN to enable private IP addresses to communicate over the Site-to-Site VPN.

![VPN](/images/6-VPNSitetoSite/vpn.png?featherlight=false&width=90pc)

## Content:

1. [Create **ASG VPN** VPC and subnet](5.1-createvpnenv/)
2. [Configure Site to Site VPN and test connection with private IP](5.2-vpnsitetosite/)
