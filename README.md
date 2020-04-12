# group-design-docs-public

Collection of example design documents that are based on either real world or lab experience. Generally the documents are thought exercises around infrastructure operations.

**Table of Contents**

- [Dell and BigSwitch Network Build Project](#Dell-and-BigSwitch-Network-Build-Project)

```
group-design-docs-public/
├── Dell-and-BigSwitch-Network-Build-Project
│   ├── BigSwitch-Datacenter-Deployment-Document
│   │   └── Datacenter-Deployment-Document-v1-0.pdf
│   ├── BigSwitch-Network-Deployment-Configuration
│   │   └── README.md
│   └── BigSwitch-Network-Deployment-Document
│       └── BigSwitch-Network-Deployment-Document-v1-1.pdf
└── README.md

```

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
