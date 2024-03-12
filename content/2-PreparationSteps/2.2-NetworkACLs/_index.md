---
title : "Network ACLs"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

## Network ACLs

- **Default Network ACL:** After VPC initialization, a default network ACL is available and can be modified. By default, it grants access to all IPv4 or IPv6 traffic entering or leaving the VPC.
- **Custom Network ACL:** You can create a custom network ACL and associate it with a subnet. By default, custom network ACLs deny all incoming and outgoing traffic until access permission rules are added.
- **Subnet Association:** Each subnet in the VPC must be associated with a network ACL. If not associated with a specific network ACL, the subnet automatically uses the default network ACL.
- **Multiple Subnets:** A network ACL can be associated with multiple subnets, but a subnet can only be linked to one network ACL at a time. Associating a new network ACL with a subnet removes the previous association.
- **Rule Sequencing:** Network ACLs have rules with sequence numbers. Rules are evaluated based on their sequence number, from lowest to highest, to determine traffic access for associated subnets. The maximum sequence number is 32766.
- **Allow/Deny Traffic:** Network ACLs contain both inbound and outbound rules for allowing or denying traffic.
- **Stateless Service:** Network ACLs are stateless; responses to allowed inbound traffic must adhere to outbound traffic rules, and vice versa.

## Network ACL Rules

You can manage rules for the default network ACL or create a new one for the VPC. Changes to the network ACL's rules automatically apply to its associated subnets.

Components of a network ACL rule:
- **Rule Number:** Rules are evaluated in sequence order, starting with the lowest number. Once a rule matches traffic, it's immediately applied even if it conflicts with higher-numbered rules.
- **Type:** Defines the traffic type (e.g., SSH). Specify traffic types or custom ranges.
- **Protocol:** Specify the protocol using standard protocol numbers.
- **Port Range:** Define the port or port range for traffic (e.g., HTTP is 80).
- **Source:** [Inbound Rule] Defines the traffic origin (CIDR range).
- **Destination:** [Outbound Rule] Specifies the traffic destination (CIDR range).
- **Allow/Deny:** Choose to Allow or Deny the specified traffic.
