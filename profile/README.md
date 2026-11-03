# Proxmox DC Sandbox

**Reproducible, datacenter-style infrastructure labs on Proxmox VE, described entirely as code.**

## Why this exists

Real datacenter patterns (SDN, EVPN/BGP, multi-layer provisioning, public IP exposure) are hard to learn and test without the hardware. This project simulates them on a single machine using nested virtualization, so anyone can deploy a complete environment from scratch, experiment, break it, and tear it down.

Every environment is a **scenario**: a self-contained lab with a clear objective, documented constraints, automated deployment and post-deployment validation. Scenarios are meant to be read, run, forked and adapted.

## Repositories

| Repository | What it is |
|---|---|
| [**core-tf-modules**](https://github.com/proxmox-dc-sandbox/core-tf-modules) | Reusable OpenTofu modules for provisioning a Proxmox VE datacenter, in three independent layers: foundation, networking, compute. Consumed through Terragrunt and pinned to immutable Git tags. |
| [**scenarios**](https://github.com/proxmox-dc-sandbox/scenarios) | Monorepo of lab scenarios built on the modules, driven by a Go orchestrator, with a template for creating new ones and a fork registry. |

## How it fits together

core-tf-modules provides the building blocks (underlay, overlay, tenant VMs and containers). Each scenario assembles them, pinned to a released tag, and adds its own automation, tests and documentation. A scenario can be deployed from a clean host with a single container, without installing anything locally.

## Design principles

- **Reproducible**: pinned versions, deliberate upgrades.
- **Portable**: no hardcoded credentials, configuration owned by the consumer.
- **Disposable**: deploy, experiment, destroy.
- **Documented**: each scenario explains its objective, architecture and limits.

## Status

Early stage. Modules are at `v0.1.0`, and the first scenario is an EVPN + BGP networking lab. More scenarios will follow.

## Get involved

Issues, forks and ideas are welcome. See the `CONTRIBUTING.md` of each repository, and `SECURITY.md` to report a vulnerability.
