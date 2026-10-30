# FutureGuard – Zero Trust Smart IoT Network

## 📌 Project Overview
FutureGuard is an advanced, simulated smart building network designed using Cisco Packet Tracer. It implements Zero Trust-inspired security principles by isolating network segments and enforcing strict Access Control Lists (ACLs). The project demonstrates the secure integration of IoT devices, enterprise routing, and network segmentation within a modern corporate infrastructure.

## 🛠️ Technologies & Protocols Used
*   **Routing & Switching:** Inter-VLAN Routing (Router-on-a-Stick), 802.1Q Trunking
*   **Network Segmentation:** VLANs (Virtual Local Area Networks)
*   **IP Addressing:** DHCP Server Configuration for dynamic allocation
*   **Security:** Extended Access Control Lists (ACLs) / Zero Trust Policies
*   **IoT Integration:** Centralized IoT Management Server, Smart Devices (Sensors, Lights, Doors)

## 🏗️ Network Topology & IP Addressing Plan
The network is logically segmented into four distinct VLANs to prevent unauthorized lateral movement and limit the attack surface:

| VLAN ID | Department / Purpose | Network Address | Default Gateway |
| :--- | :--- | :--- | :--- |
| **10** | Administration | 192.168.10.0/24 | 192.168.10.1 |
| **20** | Employees | 192.168.20.0/24 | 192.168.20.1 |
| **30** | IoT Devices | 192.168.30.0/24 | 192.168.30.1 |
| **40** | Server Network | 192.168.40.0/24 | 192.168.40.1 |

## 🔒 Security Policies (Zero Trust Implementation)
Strict ACLs are deployed on the central router to enforce the following access control policies:
1.  **Administration (VLAN 10):** Full access to all networks for management purposes.
2.  **Employees (VLAN 20):** Access granted *only* to the Server Network. Access to the Administration and IoT networks is explicitly **blocked**.
3.  **IoT Devices (VLAN 30):** Access granted *only* to the IoT Management Server. Lateral communication to other VLANs is **blocked** to prevent compromised devices from infecting the corporate network.

## 🧪 Testing & Verification
Network security policies were rigorously verified using ICMP packets in Packet Tracer's Simulation mode:
*   ✅ `Admin PC -> IoT Server` : **Successful**
*   ✅ `Employee PC -> IoT Server` : **Successful**
*   ❌ `Employee PC -> Admin PC` : **Blocked (by ACL)**
*   ❌ `IoT Device -> Admin PC` : **Blocked (by ACL)**

## 🚀 How to Run the Simulation
1. Clone the repository and download the `.pkt` file.
2. Open the file using **Cisco Packet Tracer**.
3. Navigate to the **Simulation Panel**.
4. Use the "Add Simple PDU" tool to test communication between different VLANs and observe the ACL rules actively filtering traffic at the router.
