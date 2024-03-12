---
title : "Security Group"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

## Security Group

### Basic Features of Security Group

- **Allow Rules Only:** Only Allow rules can be added; Deny rules cannot be added.
- **Separate Rules for Traffic:** Separate rules can be specified for outgoing and incoming traffic.
- **Initial Inbound Rules:** A newly created Security group starts with no Inbound rules. Initially, the instance won't allow any traffic in, requiring the addition of an Inbound rule to enable access.
- **Default Outbound Rule:** By default, the Security group includes an Outbound rule that permits all traffic to leave the instance. This rule can be modified or replaced with specific Outbound rules to control outgoing traffic originating from the instance. If there's no Outbound rule, no traffic is allowed to exit the instance.
- **Stateful Service:** Security groups are stateful services, meaning that if incoming traffic is allowed, outgoing traffic is automatically permitted, and vice versa, regardless of the Outbound rule.
- **Instance Communication:** Instances can communicate only if they are associated with a Security group that permits connections, or if a Security group associated with the instance contains a rule allowing traffic. The default Security group has default rules allowing all traffic.
- **Association with Network Interfaces:** Security groups are associated with network interfaces. After initialization, you can change the Security group assigned to an instance, which will also update the Security group for the corresponding primary network interface.

## Security Group Rule

A Security group rule is created to grant access to traffic entering or leaving an instance. This access can apply to a specific CIDR or to a Security group in the same VPC, or even to a Security group in another VPC connected by peering.

### Components of Security Group Rule

- **Inbound Rules:** These include the source of the traffic and the destination port or port range. The source can be another security group, an IPv4 or IPv6 CIDR range, or an IPv4/IPv6 address.
- **Outbound Rules:** These include the destination of the traffic and the destination port or port range. The destination can be another security group, an IPv4 or IPv6 CIDR range, an IPv4/IPv6 address, or a service identified by a prefix (e.g. igw_xxx) in the prefix ID list (where services are identified by the prefix ID - the name and ID of the available service in the region).
- **Standard Protocols:** Each protocol has a standard protocol number associated with it. For instance, SSH is associated with port number 22.
