# GNS3 Campus VLAN Network Lab

## Project Overview

This project demonstrates a robust, hierarchical campus network topology simulated within GNS3. The design focuses on Layer 2 and Layer 3 segmentation using VLANs to ensure scalability, security, and efficient broadcast domain management. The environment integrates Cisco IOU (IOS on Unix) images and utilizes a dedicated GNS3 VM for high-performance emulation.

## Topology Architecture

The network follows the industry-standard three-tier hierarchical model:

* **WAN Edge Layer** (2 Routers): Dual edge routers connected to separate ISP Cloud nodes. This simulates a Redundant WAN environment, providing failover capabilities for internet and external connectivity.

* ***Collapsed Core & Distribution Layer** (2 Multilayer Switches): Combines the routing power of the Core with the policy-based connectivity of the Distribution layer. These nodes handle Inter-VLAN routing, security filtering, and high-speed switching.

* **Access Layer**: Provides endpoint connectivity for users and workgroups. This layer is where VLANs are assigned to physical or virtual ports and where Port Security is typically enforced.

## Network Components

|Device       | Image/Platform  | Role                                   |
|-------------|-----------------|----------------------------------------|
| Edge R1 & R2|Cisco IOU L3     | Redundant WAN Edge                     |
| CD 1 & 2    |Cisco IOU L2     | Layer 3 Routing & Aggregation          |
| ACC 1 - 6   |Cisco IOU L2     | EndPoint Connectivity                  |
| RM          |Cisco IOU L3     | Out of Band Management Edge            |
| OOB         |Gns3 Cloud Vm    | Bridge to home network                 |
| SP 1 & 2    |Gns3 Cloud VM    | Provide Connection to the Internet     |
| ServiceCloud|Gns3 Cloud VM    | Link Windows server running dhcp/dns   |

## Lab Host & Automation

To manage the network programmatically, the lab includes OOB Management connection

**VM**: Ubuntu Linux
**Orchestration**: *Ansible* for configuration management and automated node deployment.
**Provisioning**: *Vagrant* used to define and manage the lifecycle of the automation host.
**Workflow**: Allows for "Infrastructure as Code" testing, including push-button configuration of VLANs across the switch fabric.
