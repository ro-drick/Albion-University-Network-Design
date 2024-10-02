# Albion University Network Topology Design

## Project Overview

This project simulates the **network architecture** for **Albion University**, which consists of a **main campus** and a **smaller branch campus**, located 20 miles apart. The design focuses on ensuring seamless communication, security, and network efficiency across the university’s **administrative departments**, **faculties**, and **student labs** using **Cisco Packet Tracer**. 

The network is built to support VLAN segmentation, dynamic IP addressing, inter-VLAN routing, and secure network access. Routing between campuses is facilitated by **RIPv2**, and external communication to a cloud-hosted email server is handled via static routing.

---

## Objectives and Requirements

Albion University’s network needs to accommodate **four faculties** spread across multiple buildings on the main campus and the **Faculty of Health and Sciences** at the smaller campus. The network design ensures:
- **Logical network segmentation** using **VLANs**.
- **Secure and dynamic IP address assignment** via **DHCP**.
- **Scalable routing** with **RIPv2** for internal routing and static routing for external servers.

### Specific Requirements:
- **Main Campus**:
  - **Building A**: Hosts the **administrative staff** (HR, Finance, and Management) and the **Faculty of Business**. VLANs are set up to segment the network traffic of each department.
  - **Building B**: Contains the **Faculty of Engineering and Computing** and the **Faculty of Art and Design**, each on its own VLAN.
  - **Building C**: Houses the **student labs** and the **IT department**, which manages the university’s internal **web server** and other critical servers.
  
- **Smaller Branch Campus**:
  - Houses the **Faculty of Health and Sciences**, with staff and student labs segmented into separate VLANs on different floors.

Each faculty and department is configured with its own subnet and VLAN to ensure logical separation of network traffic.

---

## Technologies and Configurations

This project utilizes a wide range of **networking technologies** and configurations. Below is an outline of the key components:

### 1. **Hierarchical Network Design**
   - A structured, layered design to ensure scalability and simplified management.
  
### 2. **VLAN Configuration**
   - VLANs are used to logically separate network traffic by department, faculty, and lab across both campuses.
     - **Building A VLANs**: HR, Finance, Management, Business.
     - **Building B VLANs**: Engineering, Art and Design.
     - **Building C VLANs**: IT Department, Student Labs.
     - **Branch Campus VLANs**: Health and Sciences (separate VLANs for staff and students).

### 3. **Subnetting and IP Addressing**
   - The network is subnetted to allocate appropriate IP ranges for each VLAN.
   - Example IP ranges:
     - **HR VLAN**: 192.168.10.0/24
     - **Finance VLAN**: 192.168.20.0/24
     - **Business VLAN**: 192.168.30.0/24
     - **Student Labs VLAN**: 192.168.40.0/24

### 4. **DHCP Configuration**
   - The **DHCP server** (configured on the router) dynamically allocates IP addresses to devices in **Building A**.

### 5. **Inter-VLAN Routing**
   - **Router-on-a-Stick**: A router is configured with sub-interfaces to handle **Inter-VLAN routing**, enabling communication between VLANs.

### 6. **RIPv2 Routing Protocol**
   - **RIPv2** is implemented to manage routing between different network segments across the main and branch campuses.


### 7. **Network Cabling**
   - Correct cabling, including **Ethernet**, **serial**, and **fiber optic connections**, ensures efficient communication between all devices.

---

## Network Topology

Below is the visual representation of the **Albion University Network Topology**.

*(Include the image of the network topology diagram here or a link to the image.)*

### **Main Campus**:
- **Building A**: VLANs for **administrative departments** and **Faculty of Business**.
- **Building B**: VLANs for **Faculty of Engineering and Computing** and **Faculty of Art and Design**.
- **Building C**: VLANs for **Student Labs** and the **IT Department**.

### **Smaller Branch Campus**:
- VLANs for **Faculty of Health and Sciences**, with separate VLANs for staff and students.

---

## Key Configurations and Commands

Here are some key configuration examples used in the project:

### VLAN Creation:
```bash
Switch(config)# vlan 10
Switch(config-vlan)# name HR_VLAN
Switch(config)# vlan 20
Switch(config-vlan)# name Finance_VLAN
```

### Inter-VLAN Routing (Router-on-a-Stick):
```bash
Router(config)# interface g0/0.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config)# interface g0/0.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.20.1 255.255.255.0
```

### DHCP Configuration:
```bash
Router(config)# ip dhcp pool ADMIN_POOL
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
```

### Switchport Security:
```bash
Switch(config)# interface f0/1
Switch(config-if)# switchport mode access
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 2
Switch(config-if)# switchport port-security violation restrict
```

### RIPv2 Routing:
```bash
Router(config)# router rip
Router(config-router)# version 2
Router(config-router)# network 192.168.10.0
Router(config-router)# network 192.168.20.0
Router(config-router)# no auto-summary
```

---

## Testing and Verification

- **Ping Tests**: Used to verify connectivity between VLANs and campuses.
- **Traceroute**: Ensures proper routing between network segments.
- **Port-Security Tests**: Validates security by simulating unauthorized device connections.
  
### Example Ping Test:
```bash
PC> ping 192.168.20.2
Reply from 192.168.20.2: bytes=32 time=20ms TTL=64
```

---

## How to Use the Project

1. **Download** the `.pkt` (Packet Tracer) file from the repository.
2. **Open** the file in **Cisco Packet Tracer**.
3. **Examine** the network topology, configurations, and connectivity tests.
4. **Modify** the design and configurations as needed for further learning or testing.

---

## Conclusion

This project demonstrates a scalable, secure, and efficient network topology for **Albion University**, meeting all the functional and security requirements for a modern educational institution. The use of VLANs, dynamic IP addressing, RIPv2 routing, and SSH-based secure access ensures seamless communication between faculty, students, and staff across multiple campuses.

---


## Project Files

- **[Network Topology Diagram](path_to_image)**: The complete diagram of the network design.
- **[Packet Tracer File](path_to_packet_tracer_file)**: Download the Cisco Packet Tracer `.pkt` file here.

