## Homelab Infrastructure Platform

This repository documents my multi-node self-hosted infrastructure environment built to explore systems engineering, 
observability, virtualization, and distributed service deployment using low-power hardware.

The lab functions as a miniature production-style platform supporting media services, private cloud storage, monitoring 
pipelines, and DNS-level network control.

## Infrastructure Goals

This homelab is designed to:

* simulate production-style service distribution
* practice infrastructure monitoring workflows
* experiment with virtualization and containerized deployments
* build experience with persistent storage planning
* operate privacy-preserving self-hosted services
* prepare for future infrastructure automation and orchestration

## Hardware Inventory

## OptiPlex Node 1 — Virtualization Host

Specs

* 16GB RAM
* 256GB NVMe SSD
* Running Proxmox

Responsibilities

Hosts virtualized workloads:

* Jellyfin
* Nextcloud

Proxmox enables workload isolation, snapshot support, and flexible service migration between nodes.

## OptiPlex Node 2 — Application Services Node

Specs

* 8GB RAM
* 256GB SATA SSD
* Running Ubuntu Server

Responsibilities

Dedicated application host:

* Immich

This node isolates indexing-heavy media workloads from virtualization infrastructure.

## Raspberry Pi 5 — Observability + Network Services Node

Specs

* 4GB RAM
* Raspberry Pi 5
* 1TB NVMe storage

Responsibilities

Runs infrastructure-level monitoring and DNS services:

* Pi-hole
* Prometheus
* Grafana
* cAdvisor
* node_exporter

Acts as the visibility and control layer of the homelab network.
