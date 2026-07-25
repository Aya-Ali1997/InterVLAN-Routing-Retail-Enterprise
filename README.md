
# Enterprise Hybrid Network: Inter-VLAN Routing & Dynamic DHCP Deployment

## 📌 Project Overview
This project demonstrates the design and configuration of a secure, segmented corporate network for a medium-sized retail company based in Berlin. The infrastructure utilizes **VLANs** to isolate network traffic across three core departments for enhanced security and organizational management, implementing **Router-on-a-Stick** architecture for inter-VLAN routing, and centralized automated address allocation using **DHCP**.

---

## 🏗️ Topology & Architecture
* **Core Router:** Cisco 4331 Router
* **Central Switch:** Cisco 2960 Catalyst Switch
* **Network Segmentation:**
  * **VLAN 10 (Management):** Subnet `192.168.10.0/26` | Gateway: `192.168.10.1`
  * **VLAN 20 (Finance):** Subnet `192.168.10.64/26` | Gateway: `192.168.10.65`
  * **VLAN 30 (Engineering):** Subnet `192.168.10.128/26` | Gateway: `192.168.10.129`

---

## 🛠️ Key Configurations Implemented

### 1. Switch Configuration (VLANs & Trunking)
* Created and named targeted functional VLANs.
* Scaled interface management using `interface range` commands for rapid device provisioning.
* Enabled **IEEE 802.1Q Trunking** on the backbone link interface connecting to the main router.

### 2. Router-on-a-Stick (Inter-VLAN Routing)
* Developed logical Sub-interfaces (`.10`, `.20`, `.30`) on the physical router interface.
* Bound each sub-interface to its respective VLAN encapsulation protocol tag (`encapsulation dot1Q`).

### 3. Dynamic IP Allocation (DHCP Pools)
* Configured dedicated automated router-bound DHCP IP pools matching each subnet constraint.
* Enabled automatic provisioning of IP address leases, Subnet Masks, and Default Gateways directly to endpoints upon network entry.

---

## 🔍 Verification & Troubleshooting Commands Used
To validate the reliability and operability of the deployment, the following standard Cisco IOS commands were executed and passed:
* `show vlan brief` - Certified proper port allocation and status mapping.
* `show ip interface brief` - Verified functional logic on sub-interfaces.
* `show ip route` - Evaluated operational routing tables and verified inter-departmental end-to-end ping testing.

---

## 🚀 Future Roadmap (AWS Cloud Integration)
The next evolution of this deployment aims to transform this setup into a **Hybrid Cloud Infrastructure**. This on-premise headquarters environment will safely interconnect with **AWS Munich/Frankfurt Regions** utilizing **AWS Site-to-Site VPN** or **AWS Direct Connect**, bridging physical localized subnets with an isolated AWS VPC hosting scalable enterprise compute infrastructure (EC2) and storage solutions (S3).
