# ENCS304 – Computer Networks  
## Assignment 1: Basic Network Topologies Using Switches and Hubs  

---

## Student Details  

- **University:** K.R. Mangalam University  
- **Program:** B.Tech CSE (AI & ML) – SOET  
- **Student Name:** Uma Mishra  
- **Roll Number:** 2301730304   
- **Subject Code:** ENCS304  
- **Submitted To:** Mr. Aijaz Mohammed  

---

## Experiment Title  

**Basic Network Topologies Using Switches and Hubs**

---

## Objective  

The objective of this experiment is to design and analyze different LAN topologies using Cisco Packet Tracer.  

This experiment helps in understanding:

- The behavior of Star, Bus-like, and Ring-like topologies  
- IPv4 addressing and subnetting  
- ICMP communication using ping  
- Collision domains and broadcast domains  
- Fault tolerance using Spanning Tree Protocol (STP)  

---

## Software Used  

- Cisco Packet Tracer  

---

## IP Addressing Scheme  

All PCs were configured using the following IPv4 scheme:
Network: 192.168.10.0/24
Subnet Mask: 255.255.255.0

PC0 – 192.168.10.1
PC1 – 192.168.10.2
PC2 – 192.168.10.3
PC3 – 192.168.10.4


---

## Task 1: Star Topology (Switch-Based Network)

### Configuration

- 1 Switch  
- 4 PCs connected directly to the switch  
- All PCs assigned IP addresses in the same subnet  
- Connectivity verified using ICMP ping  

### Observation

When PC0 pings PC1, the switch dynamically learns the MAC addresses of connected devices.  
The ICMP packet flows as:
PC0 → Switch → PC1

Other PCs (PC2, PC3) do not receive the traffic.

### Key Insight

- Each port on a switch is its own collision domain  
- Communication is efficient and collision-free  
- However, the switch acts as a single point of failure  

---

## Task 2: Bus-like Topology (Hub-Based Network)

### Configuration

- 1 Hub  
- 4 PCs connected to the hub  
- Same IP addressing scheme used  

### Observation

When multiple PCs send data simultaneously:

- Packet Tracer shows collisions (fire/explosion icon)  
- Hub creates a single collision domain  
- Only one device can successfully transmit at a time  

### Key Insight

- Hubs broadcast frames to all devices  
- High collision probability  
- Lower performance compared to switch-based topology  

---

## Task 3: Ring-like Topology (Switch Loop with STP)

### Configuration

- 3 Switches connected in a loop  
- 1–2 PCs connected to each switch  
- STP enabled by default  

### Observation

- All switches are physically connected in a loop  
- Spanning Tree Protocol (STP) blocks one redundant port (shown in orange) to prevent logical loops  
- Data is forwarded through active (green) ports  

### Key Insight

- Provides redundancy  
- Prevents broadcast storms  
- Eliminates logical loops automatically  

---

## Task 4: Failure Test (Link Break in Ring Topology)

### Configuration

- One active link between switches was manually disconnected  

### Observation

- Initially, ping fails because the primary path is broken  
- STP detects topology change  
- Previously blocked (orange) port transitions to forwarding (green) state  
- Communication is restored automatically  

### Key Insight

- Ring-like topology provides fault tolerance  
- Network automatically “heals” without manual reconfiguration  
- Redundant links prevent complete network failure  

---

## Comparison of Topologies

| Feature | Star (Switch) | Bus-like (Hub) | Ring-like (Switch Loop) |
|----------|---------------|----------------|--------------------------|
| Collision Domain | Separate per port | Single | Separate per port |
| Performance | High | Low | High |
| Fault Tolerance | Low | Very Low | High |
| Cost | Moderate | Low | Higher |
| Loop Protection | Not needed | Not applicable | STP required |

---

## Conclusion

This experiment demonstrates that:

- Star topology offers efficient, collision-free communication but suffers from a single point of failure.  
- Bus-like topology using a hub creates collisions due to a shared collision domain and is less efficient.  
- Ring-like topology provides redundancy and fault tolerance using Spanning Tree Protocol (STP).  

The failure test clearly shows that redundant network designs allow automatic recovery when a link fails.

Therefore, topology selection depends on balancing cost, performance, and fault tolerance requirements in real-world LAN design.

---

## Files Included in Submission

---

## How to Open and Test

1. Open `exp1_topologies.pkt` using Cisco Packet Tracer.  
2. Verify IP addresses in each PC.  
3. Use Command Prompt in PCs to run:
4. Switch to Simulation Mode to observe packet flow.  
5. For Task 4, disconnect a switch link and observe STP reconvergence.
