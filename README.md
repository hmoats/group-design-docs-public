# group-design-docs-public

Collection of example design documents that are based on either real world or lab experience. Generally the documents are thought exercises around infrastructure operations.

**Table of Contents**

- [The Enterprise or Datacenter Services as Layers](The-Enterprise-or-Datacenter-Services-as-Layers)
- [Dell and BigSwitch Network Build Project](#Dell-and-BigSwitch-Network-Build-Project)
- [Enterprise Office Build Project1](#Enterprise-Office-Build-Project1)

**Folders**

```
group-design-docs-public/
├── Cisco-L3-Spine-Leaf-Network-Build-Project
│   └── Cisco-L3-Spine-Leaf-Network-Build-Project-Top.PNG
├── Dell-and-BigSwitch-Network-Build-Project
│   ├── BigSwitch-Datacenter-Deployment-Document
│   │   └── Datacenter-Deployment-Document-v1-0.pdf
│   ├── BigSwitch-Network-Deployment-Configuration
│   │   └── README.md
│   └── BigSwitch-Network-Deployment-Document
│       └── BigSwitch-Network-Deployment-Document-v1-1.pdf
├── Enterprise-Office-Build-Project1
│   └── Enterprise-Office-Build-Floorplan-Project1.pdf
└── README.md
```
## The Enterprise or Datacenter Services as Layers

Just like the OSI model, we can consider any infrastructure build in layers. Each layer depends on each other layer and ultimately comprise a system that can be documented, controlled, monitored and secured.

**Design layers and their considerations**

- Physical

  The floor plan provides the underlay to map the MDF, IDFs, server room, cable plant and various network and security services to their ideal location based on the physical attributes. Included in the physical layer are the physical delivery systems, e.g., shipping, storage, generators, uninterruptible power supply, ingress/egress access, cable plant

- Network

  The network design should provide resilient, fast and secure layer to snap in various enterprise services, e.g., LAN, WAN, voice, video, IT services, security services, IoT, guest services, monitoring, etc. The network should be flexible and built in a way to scale and plug in future services. This layer should also consider any ingress/egress connectivity to private or public cloud services along with inter-office communication.

- Security

  The security design should provide secure access with a least privilege model. The layer of security services is wide and begins with physical and ends with deep packet inspection. The goal here is to use industry best practice security for both physical and logical systems in coordination with your company's security team to deliver sensible solution for the enterprise. Typically this layer includes: ingress/egress access systems, video systems, physical and environmental alarms, network segmentation, network surveillance, egress proxy, edge network security, etc.

- Monitoring

  A consideration that is typically off the radar is how you will monitor the telemetry from these various enterprise systems and split their streams to the appropriate teams and/or service providers to guarantee visibility and availability.

- BCP

  Finally, how does the entire system fit into the company's BCP and what needs to be provided, such as runbooks, alerts and testing, of these systems to ensure we are ready for any disaster.

## Dell and BigSwitch Network Build Project

An example project that should cover all aspects of a datacenter and network infrastructure deployment.

#### Design Goals

- BigSwitch network OS with two controllers
- Small starter footprint of 4 racks (128 1RU servers) expandable to 16 (512)
- 3 spines expandable to 4
- 40Gbps spine to leaf links (can be upgraded to 100Gbps)
- MLAG edge ports
- 1Gbps external ingress/egress
- Less than $400,000 USD

#### Documentation

- [BigSwitch Datacenter Deployment Document](https://github.com/hmoats/group-design-docs-public/blob/master/Dell-and-BigSwitch-Network-Build-Project/BigSwitch-Datacenter-Deployment-Document/Datacenter-Deployment-Document-v1-0.pdf) 

	*Floorplan | Elevation Compute | Elevation Network*
- [BigSwitch Network Deployment Document](https://github.com/hmoats/group-design-docs-public/blob/master/Dell-and-BigSwitch-Network-Build-Project/BigSwitch-Network-Deployment-Document/BigSwitch-Network-Deployment-Document-v1-1.pdf)

	*Design Goals | Physical Layer 1 | Logical Layer 2 and 3*
- [BigSwitch Network Deployment Configuration](https:////github.com/hmoats/group-design-docs-public/blob/master/Dell-and-BigSwitch-Network-Build-Project/BigSwitch-Network-Deployment-Configuration/README.md)

	*BSN Fabric Configuration*

#### Cost Estimates

Please note that these are estimates for the network kit BoM. This does not include datacenter, compute or storage costs. The price includes a 3 years of support. 

| Item | Quantity | Unit Cost | Total |
| --- | --- | --- | --- |
| Spine Switches (includes optics) | 3 | $15,000 | $45,000 |
| Leaf Switches | 8 | $10,000 | $80,000 |
| Edge Switches | 2 | $5,000 | $10,000 |
| Edge Routers | 2 | $10,000 | $20,000 |
| Virtual Host | 2 | $5,000 | $10,000 |
| BigSwitch Controller VM | 2 | $3,500 | $7,000 |
| BigSwitch Leaf License | 8 | $9,000 | $72,000 |
| BigSwitch Spine License | 2 | $15,000 | $30,000 |
| Palo Alto 850 | 2 | $9,000 | $18,000 |
| F5 I-2600 | 2 | $13,000 | $26,000 |
| APC Racks | 5 | $2,000 | $10,000 |
| APC PDUs | 10 | $1,500 | $10,500 |
| APC Misc Parts | 1 | $5,000 | $5,000 |
| Misc Cables and Parts | 1 | $10,000 | $10,000 |

Total: $353,500

## Enterprise Office Build Project1

Enterprise example office project1. 

### Documentation

- [Enterprise Office Build Floorplan Project1](https://github.com/hmoats/group-design-docs-public/blob/master/Enterprise-Office-Build-Project1/Enterprise-Office-Build-Floorplan-Project1.pdf)
- [Enterprise Office Build Elevation Project1](https://github.com/hmoats/group-design-docs-public/blob/master/Enterprise-Office-Build-Project1/Enterprise-Office-Build-Elevation-Project1.pdf)
- [Enterprise Office Build Layer1 Project1](https://github.com/hmoats/group-design-docs-public/blob/master/Enterprise-Office-Build-Project1/Enterprise-Office-Build-Layer1-Project1.pdf)
- [Enterprise Office Build Layer3 Project1](https://github.com/hmoats/group-design-docs-public/blob/master/Enterprise-Office-Build-Project1/Enterprise-Office-Build-Layer3-Project1.pdf)
