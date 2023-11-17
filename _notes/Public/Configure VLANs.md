---
title: OpenWRT Configure VLANs
feed: show
date: 2021-11-01
---

VLANs are configured in OpenWRT per [[Server]]. These can be physical ports, bridges or virtual Ethernet interfaces. To configure a [[VLAN]], navigate to *Network/Interfaces/Devices*. 

# Tagged VLAN for Bridge Networks

*Configure* the device, where you want to enable VLAN and go to *Bridge VLAN filtering*. There, tick *Enable VLAN filtering* and add VLAN Ids. Then you can select on which bridged device the respective VLANs shall be available and how they shall be transmitted:

| Option               | Despcription                           |
| -------------------- | -------------------------------------- |
| Do not participate   | Port not used.                         |
| Egress untagged (u)  | Tag of the selected VLAN gets removed. |
| Egress tagged (t)    | Traffic is transmitted with VLAN tag.  |
| Primary VLAN ID (\*) | Incomming packets without tag will get this VLAN id.                                       |

> [!WARNING]
> Before saving and applying the changes, you need to change device of the interface you are currently connected to (as long as you enabled VLAN on the respective device). Otherwise, you will lock yourself out.

To select the correct VLANs for your interfaces go to *Interfaces* and edit the device to be *\<bridge name\>.\<vlan id\>* of the desired [[OpenWRT Interface|Interface]]. Then you can save any apply all changes.
