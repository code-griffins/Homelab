Homelab Infrastructure Portfolio

Overview

This repository documents the architecture, design decisions, and evolution of my self-hosted homelab environment. The goal of this project is to gain hands-on experience with infrastructure engineering, service orchestration, storage planning, and networking while building a reliable personal platform for experimentation and production-grade self-hosted services.

The lab currently runs across multiple small-form-factor nodes and a Raspberry Pi, connected through a gigabit network switch and organized into a compact rack setup.

⸻

Hardware Inventory

Compute Nodes

Node 1

* Model: Dell OptiPlex Micro
* RAM: 16 GB
* Storage: 256 GB NVMe SSD
* Role: Primary services node (planned)

Node 2

* Model: Dell OptiPlex Micro
* RAM: 8 GB
* Storage: 256 GB SATA SSD
* Role: Media + photo infrastructure node

Node 3

* Model: Raspberry Pi 5
* RAM: (fill in)
* Storage: 1 TB NVMe SSD
* Role: Storage / lightweight services / experimentation node

⸻

Physical Layout (Current + Planned)

The homelab currently runs as a compact multi‑node desktop cluster connected through a gigabit switch. A small rack enclosure (DeskPi RackMate or similar) is planned to improve cable management, airflow, and modular expansion as the system grows.

Current physical stack:

* OptiPlex node (16 GB)
* OptiPlex node (8 GB)
* Raspberry Pi 5
* 8‑port gigabit switch

Planned rack additions:

* Rack enclosure for structured mounting
* Patch panel for cable organization
* Dedicated NAS node (future)
* Firewall appliance (future)
* UPS power backup

⸻

Network Topology

Layout

ISP Router
→ Gigabit Switch
→ OptiPlex Node 1
→ OptiPlex Node 2
→ Raspberry Pi 5

The switch acts as the central internal distribution layer for all compute nodes.

Design Goals

* Allow east‑west traffic between nodes
* Support service migration between machines
* Prepare for VLAN segmentation later
* Enable centralized storage access

⸻

Storage Strategy

Current Allocation

Device	Storage	Purpose
OptiPlex (16 GB)	NVMe SSD	Primary compute workloads
OptiPlex (8 GB)	SATA SSD	Immich photo storage
Raspberry Pi 5	1 TB NVMe	Bulk storage / future NAS role

Rationale

NVMe storage is prioritized for latency‑sensitive workloads such as container services and indexing tasks.

High‑capacity storage is centralized on the Raspberry Pi node to prepare for shared storage across services.

⸻

Services Currently Running

Immich (Self‑Hosted Photo Platform)

Purpose:

Provides a private Google Photos–style backup and browsing system for personal media.

Deployment reasoning:

Runs on the 8 GB node to isolate storage‑heavy workloads from compute‑heavy services.

Benefits:

* Local photo ownership
* Faster indexing than cloud sync
* No subscription dependency

⸻

Planned Services Roadmap

The homelab is designed as an expandable infrastructure platform. Planned additions include:

Storage Layer

* Central NAS service
* Automated backups
* Snapshot support

Networking

* VLAN segmentation
* Internal DNS
* Reverse proxy entry point

Observability

* Metrics dashboard
* Log aggregation
* Node health monitoring

AI Infrastructure

* Local LLM inference workloads
* Model serving experiments
* Private automation assistants

⸻

Service Placement Strategy

Services are distributed based on workload characteristics:

Service Type	Placement Logic
Storage‑heavy	Raspberry Pi node
Media indexing	8 GB OptiPlex
Compute workloads	16 GB OptiPlex

This separation improves reliability and allows independent scaling.

⸻

Networking Upgrade Path

Planned improvements:

1. Introduce managed switch features
2. Segment services with VLANs
3. Add firewall appliance
4. Enable secure remote access

These changes will transition the homelab toward a production‑style internal architecture.

⸻

Reliability Strategy

Planned reliability improvements include:

* Scheduled backups
* Service restart automation
* Storage redundancy
* Configuration version control

⸻

Lessons Learned So Far

Small form factor enterprise desktops provide excellent price‑to‑performance infrastructure nodes.

Separating storage workloads from compute workloads improves responsiveness.

Running services locally provides more control over performance, privacy, and upgrade cycles.

Designing infrastructure incrementally makes scaling decisions easier over time.

⸻

Future Architecture Vision

The long‑term goal is to evolve this homelab into a miniature production‑style platform featuring:

* Centralized storage
* Container orchestration
* Automated deployment workflows
* Observability stack
* Secure service exposure

This environment serves as a hands‑on infrastructure engineering lab for experimenting with distributed services, networking concepts, and self‑hosted platforms.
